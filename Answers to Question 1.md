Concerns:
  1. Security - Security concerns are of the highest priority because normally, they're not unit tested thoroughly and accessing
     someone's private repos with incorrect authentication would jeopardize all of github and lose customers' trust.
  2. Availability & Data Integrity - We want to know that all of our service offerings are available to customers and that 
     commits/deployments did not alter feature availability. In addition, we want to know that data extracted or updated 
     using the API works as expected. Ideally, every endpoint would be tested with a simple GET to validate the service is up.
  3. Features - Feature testing is deprecated when performing API testing as API testing is mainly concerned
     with API availability and proper authentication. In case feature testing is not covered elsewhere (unit/integration), 
     then feature testing can be performed at the API level as well.

Method:
  1. Initially, I was going to use Python Request and pyresttest https://github.com/svanoort/pyresttest 
     but, because I actually woudn't use that implementation today, I decided to show what I would actually implement at work.
  2. My implementation uses Runscope (http://runscope.com), which I briefly talked about during my interview.
  3. I use a runscope trigger URL as a github webhook to trigger a CI API test run.
  4. I've added a URL badge but this badge is static and of little use.  Runscope doesn't support Build status badges yet, so instead of adding a third service (Travis CI, Circle CI, etc) to manage Badge URLs, I simply added the static badge to demonstrate that it can easily be done using a dynamic URL from the aforementioned CI services.

Tests:
  1. The API tests will be testing two endpoints  /user and /user/repo. *The Pull Requests endpoint would also be an ideal candidate for testing.
  2. /user
    1. GET user with INvalid credentials
    2. GET user with valid credentials
    3. PATCH user with INvalid credentials
    4. PATCH user with valid credentials
  3. /user/repo
    1. GET repos of user, validate data integrity
    2. POST new repo
    3. PATCH repo description, validate success
    4. DELETE newly added repo
