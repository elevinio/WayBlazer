Concerns:
  1. Security - Security concerns are of the highest priority because normally, they're not unit tested thoroughly and accessing
     someone's private repos with incorrect authentication would jeopardize all of github and lose customers' trust.
  2. Availability & Data Integrity - We want to know that all of our service offerings are available to customers and that 
     commits/deployments did not alter feature availability. In addition, we want to know that data extracted or updated 
     using the API works as expected.
  3. Features - Feature testing is deprecated when performaing API testing as API testing is mainly concerned
     with API availability and proper authentication. In case feature testing is not covered elsewhere (unit/integration), 
     then feature testing can be performed at the API level as well.

Method:
  1. Initially, I was going to use Python Request and pyresttest https://github.com/svanoort/pyresttest 
     but, because I actually woudn't use that implementation today, I decided to show what I would actually implement at work.
  2. My implementation uses Runscope (http://runscope.com), which I briefly talked about during my interview.
  3. I use a runscope trigger URL as a github webhook to trigger a CI API test run.
  
