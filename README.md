## Prompt (SYSTEM DESIGN MODULE):
We encourage an image submission (in addition to your written response), which you can draw on a whiteboard, take a picture, and email to rpt.communication@hackreactor.com with the subject line
How would you design bit.ly, the popular URL-shortening service?
1) Please make sure to cover both shortening of long URL's and expansion of short URL's.
2) We expect some discussion of scalability failure scenarios and how those would be addressed.
Remember the Extreme Architecture lectures & exercise
Address how you would "operationalize" the system as a real business. I.e., imagine you are the CEO/founder of this URL-shortening startup and you want to grow your business as effectively as possible. How do you design the system to accommodate?

## Preliminary questions(for research):
Does bit.ly host the new domain name?
Does bit.ly have a registration of all domain names not yet taken?
Bit.ly can shorten an AWS docs url, but not a google drive url. Why?
Wikipedia:
https://en.wikipedia.org/wiki/URL_shortening
## Whiteboard:
https://awwapp.com/b/u3e6hrnqr/
## Database stores:
Hash (from which to derive key in server)
Original URL
Expiration date (optional)
Metrics for clicks. If no one has clicked for 3 months, delete with cron job.
## Stack:
React (input field)
Express
MongoDB:
SQL are vertically scalable
NoSQL are horizontally scalable, “making NoSQL databases the preferred choice for large or ever-changing data sets.” *I would expect a middleman router like this URL shortener to get a lot of traffic. This type is high-performing for simple queries (which is what we have). Let’s go NoSQL.
## Router:
GET
Redirect
POST (creating new shortened URL):
Parse POST request(the url provided)
Hash parsed url
Store in database
Return key (path added to my site’s host)
## Hash:
Probably use an npm module rather than writing function from scratch

