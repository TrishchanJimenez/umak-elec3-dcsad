# Lab 4 Submission - Group 03

## Activity Details
- Activity ID: Lab-4
- Group Name: Group 3
- User ID: dcsad-g03

## Answers to Questions

### Question 1
Both routes call the same function. How does your code know which route a request came through?
**Answer:** The Lambda function inspects the `routeKey` property within the incoming `event` object (`event.get("routeKey")`). API Gateway automatically populates this field with the matched route format (e.g., `"GET /messages"` or `"POST /messages"`), allowing the code to use conditional `if` branching to execute the corresponding route handler.

### Question 2
What answer do you get when you open the invoke URL without `/messages`? Why does API Gateway answer this way, and not your function?
**Answer:** Opening the root invoke URL returns `{"message":"Not Found"}` with an HTTP 404 status code. API Gateway responds directly because there is no route configured for `/` or `ANY /`. Since API Gateway cannot match the request to any configured route, it rejects the request at the gateway level before invoking the Lambda function.

### Question 3
Your `GET /messages` route uses Scan. What happens to the cost of each GET request as the table grows to thousands of messages? Why?
**Answer:** As the table grows to thousands of messages, the cost and latency of each `GET` request will increase significantly. A DynamoDB `Scan` operation reads every single item in the entire table rather than querying specific partition keys. DynamoDB charges read capacity units (RCUs) based on the total volume of data read from storage; therefore, scanning thousands of items consumes substantially more read capacity and increases per-request API costs.