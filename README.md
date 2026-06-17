# date-fns Complete Beginner Guide

## What is date-fns?

date-fns is a modern JavaScript library that makes working with dates much easier. Instead of writing complex date logic manually, you can use simple utility functions to format dates, calculate differences, validate dates, and perform date arithmetic.

Install date-fns:

```bash
npm install date-fns
```

---

# 1. format()

Used to display a date in a human-readable format.

### Example

```js
import { format } from "date-fns";

const date = new Date();

console.log(format(date, "dd/MM/yyyy"));
```

### Output

```txt
17/06/2026
```

### Common Patterns

```js
format(date, "dd/MM/yyyy");
```

```txt
17/06/2026
```

```js
format(date, "MMMM dd, yyyy");
```

```txt
June 17, 2026
```

```js
format(date, "EEEE");
```

```txt
Wednesday
```

```js
format(date, "hh:mm a");
```

```txt
09:30 PM
```

### Real World Use Cases

- Blog publish dates
- User registration dates
- Invoice dates
- Order history

---

# 2. parseISO()

Used to convert an ISO date string into a JavaScript Date object.

### Example

```js
import { parseISO } from "date-fns";

const dateString = "2026-06-17";

const date = parseISO(dateString);

console.log(date);
```

### Why Use It?

Most APIs return dates as strings.

```js
{
  createdAt: "2026-06-17T10:30:00Z"
}
```

Before performing date operations, convert the string into a Date object.

### Real World Use Cases

- API responses
- MongoDB timestamps
- Supabase timestamps
- Backend-generated dates

---

# 3. addDays()

Adds a specific number of days to a date.

### Example

```js
import { addDays } from "date-fns";

const today = new Date();

const nextWeek = addDays(today, 7);

console.log(nextWeek);
```

### Real World Use Cases

- Subscription expiry dates
- Trial periods
- Booking systems
- Delivery estimates

---

# 4. subDays()

Subtracts days from a date.

### Example

```js
import { subDays } from "date-fns";

const today = new Date();

const previousWeek = subDays(today, 7);

console.log(previousWeek);
```

### Real World Use Cases

- Fetching last 7 days data
- Analytics dashboards
- Reports
- Activity history

---

# 5. addMonths()

Adds months to a date.

### Example

```js
import { addMonths } from "date-fns";

const nextMonth = addMonths(new Date(), 1);

console.log(nextMonth);
```

### Real World Use Cases

- Subscription renewals
- Membership plans
- Monthly reminders
- Payment schedules

---

# 6. subMonths()

Subtracts months from a date.

### Example

```js
import { subMonths } from "date-fns";

const previousMonth = subMonths(new Date(), 1);

console.log(previousMonth);
```

### Real World Use Cases

- Monthly reports
- Historical analytics
- Revenue tracking
- Usage statistics

---

# 7. differenceInDays()

Calculates the number of days between two dates.

### Example

```js
import { differenceInDays } from "date-fns";

const startDate = new Date("2026-06-01");
const endDate = new Date("2026-06-17");

const days = differenceInDays(endDate, startDate);

console.log(days);
```

### Output

```txt
16
```

### Real World Use Cases

- Days remaining
- Project deadlines
- Event countdowns
- Subscription duration

---

# 8. differenceInMonths()

Calculates the number of months between two dates.

### Example

```js
import { differenceInMonths } from "date-fns";

const startDate = new Date("2026-01-01");
const endDate = new Date("2026-06-01");

const months = differenceInMonths(endDate, startDate);

console.log(months);
```

### Output

```txt
5
```

### Real World Use Cases

- Membership duration
- User retention analysis
- Financial reports
- Growth metrics

---

# 9. isEqual()

Checks whether two dates are exactly the same.

### Example

```js
import { isEqual } from "date-fns";

const result = isEqual(
  new Date("2026-06-17"),
  new Date("2026-06-17")
);

console.log(result);
```

### Output

```txt
true
```

### Real World Use Cases

- Date comparison
- Scheduling systems
- Calendar applications

---

# 10. isToday()

Checks whether a date is today's date.

### Example

```js
import { isToday } from "date-fns";

const result = isToday(new Date());

console.log(result);
```

### Output

```txt
true
```

### Real World Use Cases

- Chat applications
- Notification systems
- Task management apps
- Attendance systems

---

# 11. isFuture()

Checks whether a date is in the future.

### Example

```js
import { isFuture } from "date-fns";

const result = isFuture(
  new Date("2030-01-01")
);

console.log(result);
```

### Output

```txt
true
```

### Real World Use Cases

- Upcoming events
- Booking systems
- Reservation systems
- Product launches

---

# 12. isPast()

Checks whether a date is already in the past.

### Example

```js
import { isPast } from "date-fns";

const result = isPast(
  new Date("2020-01-01")
);

console.log(result);
```

### Output

```txt
true
```

### Real World Use Cases

- Expired subscriptions
- Deadline validation
- Coupon expiration
- Event history

---

# 13. formatDistanceToNow()

Shows how much time has passed since a date or how much time remains until that date.

### Example

```js
import { formatDistanceToNow } from "date-fns";

const result = formatDistanceToNow(
  new Date("2026-06-15"),
  {
    addSuffix: true,
  }
);

console.log(result);
```

### Output

```txt
2 days ago
```

or

```txt
in 5 days
```

### Real World Use Cases

- Chat applications
- Notifications
- Social media posts
- Activity feeds

---

# Real World Example: Chat Application

### MongoDB Data

```js
{
  text: "Hello",
  createdAt: "2026-06-17T10:00:00Z"
}
```

### UI Display

```js
import { formatDistanceToNow } from "date-fns";

const timeAgo = formatDistanceToNow(
  new Date(message.createdAt),
  {
    addSuffix: true,
  }
);

console.log(timeAgo);
```

### Output

```txt
5 minutes ago
```

---

# Real World Example: Blog System

### API Response

```js
{
  title: "My First Blog",
  createdAt: "2026-06-17T10:00:00Z"
}
```

### UI Display

```js
import { format } from "date-fns";

const formattedDate = format(
  new Date(post.createdAt),
  "MMMM dd, yyyy"
);

console.log(formattedDate);
```

### Output

```txt
June 17, 2026
```

---

# Most Commonly Used Functions

These functions cover most real-world frontend projects:

```js
format
parseISO

addDays
subDays

addMonths
subMonths

differenceInDays
differenceInMonths

isEqual
isToday
isFuture
isPast

formatDistanceToNow
```

---

# Quick Reference Table

| Function | Purpose |
|-----------|----------|
| format() | Format dates into readable strings |
| parseISO() | Convert ISO string to Date object |
| addDays() | Add days to a date |
| subDays() | Subtract days from a date |
| addMonths() | Add months to a date |
| subMonths() | Subtract months from a date |
| differenceInDays() | Get difference in days |
| differenceInMonths() | Get difference in months |
| isEqual() | Compare two dates |
| isToday() | Check if date is today |
| isFuture() | Check if date is in future |
| isPast() | Check if date is in past |
| formatDistanceToNow() | Show relative time |

---

# Conclusion

date-fns is one of the most popular date libraries in the JavaScript ecosystem because it is lightweight, modular, tree-shakeable, and easy to use.

For most React, Next.js, Node.js, MongoDB, and Supabase projects, learning the functions above is enough to handle the majority of date-related tasks you'll encounter in real-world applications.
