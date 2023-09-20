## The Tibet Museum Data cleaning
* Extract the year data from title column 
* run the existing python script
- deploy on a smaller scale
- ask budget for DigitalOcean/Vercel/CloudFlair

## Budget for the web site
- Vercel (https://vercel.com/)
	- For React on Next.js frontend of the application
- Planet Scale (https://planetscale.com/)
	- For managed MySQL database service
- DigitalOcean Droplet (https://www.digitalocean.com/)
	- For the backend Laravel RESTful API
- CloudFlair (www.cloudflare.com)
	- For SSL and protection against DDoS attacks
- S3 (aws.amazon.com/s3/)
	- For all Media storage
- CloudFront (aws.amazon.com/cloudfront/)
	- CDN for S3 media


# Hosing it on LaraServer
`museumbackend.cta`
This is domain for Laravel API 

`tibetmuseum.cta`
Apache Proxy for next app running on localhost:3001