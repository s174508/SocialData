# Test website locally
- Open terminal in `Hugo/SocialData`
- Run `hugo server`
- Go to `localhost:1313/SocialData` in a browser

# Update actual website
- Delete the contents of `Hugo/SocialData/docs`
- Open terminal in `Hugo/SocialData`
- Run `hugo`
- Commit and push
- Wait a few seconds for the website to update (see status in `Settings -> Pages` in the Github repository)
    - If "your site is ready to be published", it hasn't updated yet
    - If "your site is published", it has been updated
- Go to `s174508.github.io/SocialData/`

# Hacker notes
### Increase content width
- The theme (ananke) has an element called "measure-wide" that decides how wide content can be
- In the file `Hugo/SocialData/themes/ananke/assets/ananke/css/_styles.css` I've overwritten .measure-wide
- Setting its value, `max-width`, changes the maximum width of content