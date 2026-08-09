+++

title = "Using Capybara and Rspec assertions in Page Objects"
description = "Writing well encapsulated tests in Rails with the Page Object pattern"
author = "Gurpreet Luthra"
date = 2014-01-10T02:13:50Z
images = ["/images/general/orange-evening.jpg"]
aliases = [
    "/2014/01/10/using-capybara-and-rspec.html/",
    "/2014/01/10/using-capybara-and-rspec.html/"
]

tags = [
    "programming",
    "testing",
    "technical",
    "quality",
]

+++

![Near the Norbulingka Institute, Dharamshala, India](/images/general/orange-evening.jpg "Near the Norbulingka Institute, Dharamshala, India")


On my Rails project, I am using RSpec and Capybara to write functional tests.  
I did not want to specify any HTML elements in my Capybara feature files, since that makes the 
feature files brittle to HTML / CSS changes. It also violates the DRY principle and basic code hygiene.

So, I decided to refactor out my HTML centric Capybara code into separate Page Objects. If you are unfamiliar with Page Objects, then read the following:

- [Page Objects by Martin Fowler](http://martinfowler.com/bliki/PageObject.html)
- [Better Acceptance Tests with Page Objects](http://robots.thoughtbot.com/better-acceptance-tests-with-page-objects)

The Page Object pattern for encapsulating HTML centric DSL is a common pattern followed while writing UI level functional tests in ThoughtWorks.

The problem I was facing when I refactored my code into Page objects was that I was unable to use the RSpec '**expect**' syntax in Page Objects. Turns out all I had to do in my page objects was:

```ruby
include RSpec::Matchers
```

Here is the full code from my project on Github: [https://github.com/gsluthra/dakshina/tree/master/spec/features](https://github.com/gsluthra/dakshina/tree/master/spec/features)

The appropriate feature files and page objects, from [this GIST](https://gist.github.com/gsluthra/8356015):

**capsule_create_form.rb** (Page Object)

```ruby
# Page Object
class CapsuleCreateForm
  include Capybara::DSL

  def submit_form(capsule={})
    fill_in 'Title', :with => capsule[:title]
    fill_in 'Description', :with => capsule[:description]
    fill_in 'capsule_study_text', :with => capsule[:study_text]
    fill_in 'capsule_assignment_instructions', :with => capsule[:assignment_instructions]
    fill_in 'capsule_guidelines_for_evaluators', :with => capsule[:guidelines_for_evaluators]
    click_button 'Save Capsule'
  end

end
```

**capsule_view_page.rb** (Page Object)

```ruby
require 'spec_helper'

# Page Object
class CapsuleViewPage
  include Capybara::DSL
  include RSpec::Matchers

  def validate_on_page
    expect(page).to have_selector('#capsule-title-page')
    expect(page).to have_link('Edit')
  end


  def validate_capsule_data (capsule={})
    expect(page).to have_content capsule[:title]
    expect(page).to have_content capsule[:description]
    expect(page).to have_content capsule[:study_text]
    expect(page).to have_content capsule[:assignment_instructions]
    expect(page).to have_content capsule[:guidelines_for_evaluators]
  end

end
```

**capsule_feature_spec.rb** (Feature File)

```ruby
require 'spec_helper'

#Feature File

feature 'Capsules Feature' do

  let(:capsuleHash) { attributes_for(:tdd_capsule) }
  let(:capsuleForm) { CapsuleCreateForm.new }
  let(:capsuleViewPage) { CapsuleViewPage.new }

  scenario 'Add a new capsule and displays the capsule in view mode' do

    visit '/capsules/new'

    expect {
      capsuleForm.submit_form(capsuleHash)
    }.to change(Capsule, :count).by(1)

    capsuleViewPage.validate_on_page
    capsuleViewPage.validate_capsule_data(capsuleHash)

  end

end
```

_Originally posted on my older blog post here: [Using Capybara and Rspec assertions in Page Objects](http://techie-notebook.blogspot.com/2014/01/using-capybara-and-rspec-assertions-in.html)_
