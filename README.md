# sagnificent.github.io

Personal site of Sagnik Roy — Bachelor of Statistics student at the Indian
Statistical Institute, Kolkata.

Live at <https://sagnificent.github.io>.

## Structure

Static HTML, no build step. Everything lives in `index.html`; the five "pages"
(About, Resume, Projects, Coursework, Contact) are `<article>` blocks that are
shown and hidden by `assets/js/script.js`.

```
index.html          all page content
assets/css/         styling
assets/js/          page switching, project filters, contact form
assets/images/      avatar, icons, project thumbnails
cv.pdf              linked from the sidebar
```

Built on the [vCard portfolio template](https://github.com/codewithsadee/vcard-personal-portfolio)
by codewithsadee (MIT).

## Local preview

```bash
python3 -m http.server 8000
```

Then open <http://localhost:8000>.

## Previous site

The earlier Jekyll (academicpages) version of this site is preserved on the
[`academicpages-site`](../../tree/academicpages-site) branch.
