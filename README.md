# S3 Static Website Hosting

## What This Project Is

This project deploys a simple static website using AWS S3. The site is publicly accessible via the S3 website endpoint.

## AWS Services Used

- Amazon S3 (bucket, static website hosting, bucket policy)

## What I Did (Steps)

1. Created an S3 bucket named `[project-bucket-18-11-2026]` in `[N. Virginia]`.
2. Uploaded `project.html` to the bucket.
3. Enabled static website hosting in bucket properties, set index document to `project.html`.
4. Turned off "Block all public access" at the bucket level.
5. Attached a bucket policy to allow public `s3:GetObject` access.
6. Accessed the website endpoint and confirmed the page loaded.

## Problems I Hit and How I Fixed Them

**Problem:** First visit returned `403 Access Denied`.

**Cause:** The bucket policy `Resource` field had the wrong bucket name (mismatched name).

**Fix:** Corrected the bucket name in the policy to exactly match the actual bucket name. After saving, the page loaded.

## What I Learned

- S3 buckets are private by default. Public read access requires both disabling Block Public Access and a bucket policy — one without the other still returns Error 403.
- The S3 **website endpoint** (`http://project-bucket-18-11-2026.s3-website-us-east-1.amazonaws.com`) only works for publicly readable content and returns HTML.
- The website endpoint does not support HTTPS. For HTTPS, CloudFront would be needed (next step).

## Live Demo

S3 website endpoint URL - http://project-bucket-18-11-2026.s3-website-us-east-1.amazonaws.com
The above URL was later removed after testing to avoid charges.

## Notes

This project was completed following the AWS official documentation for S3 static website hosting.
