### Image
Add all the domains you are getting images from in the `next.config.js` file. This is to give the site authorization to get images from those sites.
```jsx
/** @type {import('next').NextConfig} */
const nextConfig = {
    images: {
        domains: ['m.media-amazon.com'] //allow images from amazon domain
    }
}

module.exports = nextConfig
```