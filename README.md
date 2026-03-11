# www-technologies
# Assignment 01: Understanding HTTP Protocol with curl

## Task 1: Your First GET Request
**A. What type of content did the server return?**
- The server returned data in `JSON` format (`application/json`).

**B. Where do you see the resource ID?**
- The resource ID is visible at the end of the URL (`/posts/1`) and also within the JSON response body as `"id": 1`.

**C. Can you see the HTTP status code?**
- No, using a standard `curl` command only shows the response body; the status code is hidden.

---

## Task 2: Viewing Response Headers
**D. What does 200 mean?**
- It means the request was successful (OK).

**E. What category of status code is it?**
- It belongs to the `2xx` Success category.

**F. What other codes do you know?**
- 201 (Created), 400 (Bad Request), 404 (Not Found), 500 (Internal Server Error).

---

## Task 3: Analyzing Response
**G. What would happen if Content-Type were text/html instead?**
- The browser would try to render the content as a webpage, but since it is JSON, it would appear as raw text without proper formatting.

**H. Does the content-length match the actual size of the body?**
- Yes, `content-length` represents the size of the response body in bytes.

**I. Why is Connection important in high-traffic systems?**
- It manages whether the connection stays open (keep-alive) or closes. Keeping it open reduces the overhead of repeatedly establishing new TCP connections.

---

## Task 4: Simulating HTTP Errors
**J. What status code did you receive?**
- `404 Not Found`.

**K. Is there a response body?**
- Yes, it returned an empty JSON object `{}`.

**L. How does it differ from the successful case?**
- The successful case returns code `200` with data, while this case returns `404` indicating the resource does not exist.

---

## Task 5: Sending data with POST request
**M. What status code did the server return?**
- `201 Created`.

**N. What does it mean?**
- It means the request succeeded and a new resource was successfully created on the server.

**O. What headers appear in this response?**
- Headers such as `location`, `content-type`, `content-length`, and `date` are present.

---

## Task 6: Authentication (Discussion)
**P. Does this API actually validate the token?**
- No, JSONPlaceholder is a mock API and generally accepts any token for testing purposes.

**Q. What status code would a real secure API return if the token were invalid?**
- `401 Unauthorized`.

**R. What is the difference between 401 and 403?**
- **401 Unauthorized:** The user is not authenticated (not logged in).
- **403 Forbidden:** The user is authenticated but does not have permission to access the specific resource.

---

## Task 7: Status Code Classification
**U. Complete the following table:**

| Code | Category | Meaning |
| :--- | :--- | :--- |
| 200 | Success | OK. The action was successful. |
| 201 | Success | Created. A new resource has been created. |
| 400 | Client Error | Bad Request. The server cannot process the request. |
| 401 | Client Error | Unauthorized. Authentication is required. |
| 403 | Client Error | Forbidden. Permission denied. |
| 404 | Client Error | Not Found. The resource could not be found. |
| 500 | Server Error | Internal Server Error. The server encountered an error. |

---

## Task 8: Discussion
**V. Why is it bad practice to always return 200, even on errors?**
- It misleads the client into thinking the request was successful. It breaks error handling, monitoring systems, and makes debugging very difficult.
