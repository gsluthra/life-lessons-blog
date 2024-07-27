# life-lessons-blog 

Hugo based blog (still under development).

Useful Links:
 - https://www.freecodecamp.org/news/your-first-hugo-blog-a-practical-guide/
 - https://pakstech.com/blog/blog-with-hugo/
 - https://www.thepolyglotdeveloper.com/2019/01/create-custom-shortcodes-embed-content-hugo-posts-pages/


## Command to install HUGO on Mac
```
brew install hugo
```

## Command to see blog locally
```
hugo serve -D
```

## Commands to build blog and publish to Github

```
# Get assets compiled into public folder
hugo

# Copy all assets into github io repository
cp -R public/* ~/Projects/gsluthra.github.io

# Commit & Push to github.io from that repository
```
