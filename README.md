# blog.ryanheisler.com

Clone this repository and run `npm install`

To run the full app in development mode, run `npm run frontend-dev`

To compile the files into a distributable directory which can be served from e.g. S3, `npm build`

## Update site content - 1st Draft

Currently, I'm hosting this site on AWS S3 with Cloudfront.

The following is how you can update the site with new content.

1. Run `npm run build`
2. Upload the contents of dist/public to the S3 bucket, overwriting or skipping anything that's already there.
    1. Note: if you load up the site locally, none of the assets will load because it's looking for the files at the root of the filesystem. That will work just fine once you copy it to S3.
3. Create an invalidation for the Cloudfront distribution. In Cloudfront:
    1. Open the Distribution
    2. Go to the Invalidations tab
    3. Click "Create invalidation"
    4. Put "/*" to invalidate all files, or invalidate individual files more selectively if you want.
4. When the invalidation is done processing, go to blog.ryanheisler.com and double-check your new content is present.