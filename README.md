## Task

Implement an application that accepts a collection of _shifts_ and outputs a _payslip_. Tooling, language and design is the choice of the implementor but it'd be reasonable to assume a command line executable or service endpoint or similar that takes an input and produces an output. It is **not** expected to produce a GUI for this task.

Whilst having the correct output is important, we are more interested in your approach to the solution.

### Example Input

An example of the input looks like below:

```json
{
  "employee": {
    "name": "R2-D2",
    "age": "adult",
    "casual": true
  },
  "wageLevels": {
    "1": "12.34",
    "3": "14.12"
  },
  "shifts": [
    {
      "start": "2019-06-27T12:00:00",
      "end": "2019-06-27T23:15:00",
      "wageLevel": "1",
      "breakStart": "2019-06-27T17:30:00",
      "breakDurationMinutes": "45"
    },
    {
      "start": "2019-06-28T12:00:00",
      "end": "2019-06-28T16:15:00",
      "wageLevel": "1"
    },
    {
      "start": "2019-06-29T11:00:00",
      "end": "2019-06-29T18:30:00",
      "wageLevel": "1"
    },
    {
      "start": "2019-06-30T12:00:00",
      "end": "2019-06-30T21:15:00",
      "wageLevel": "3",
      "breakStart": "2019-06-30T14:30:00",
      "breakDurationMinutes": "30"
    }
  ]
}
```

### PaySlip Rules

- For every hour worked the employee earns 1 hour of their base rate for the shifts `wageLevel`.
- Employee's do not earn anything during breaks.
- Breaks may be `30`, `45` or `60` minutes.
- If the employee is casual they earn an additional loading of `25%` for every hour worked.
- For hours worked after 6pm from Monday to Friday the employee earns an additional loading of `30%` (inclusive of the casual loading).
- Hours beyond 9 hours of work (excluding breaks) are considered overtime.
- For hours worked as overtime the employee earns an additional overtime loading of `75%` (inclusive of the casual loading).
- For hours worked beyond 3 hours of overtime the employee earns an additional overtime loading of `125%` (inclusive of the casual loading).
- For hours worked on a Saturday the employee earns an additonal loading of `50%` (inclusive of the casual loading).
- For hours worked on a Sunday the employee earns an additional loading of `95%` (inclusive of the casual loading).
- For overtime hours worked on a Sunday the employee earns an additional loading of `125%`
- For hours worked on a Public Holiday the employee earns an additional loading of `150%` (inclusive of the casual loading).
- For overtime hours worked on a Public Holiday the employee earns an additional loading of `175%` (inclusive of the casual loading).
- If an employee works for more than 5 hours without a break they are entitled to a crib allowance of `50%` of thier base rate.

### PaySlip format

- The payslip should provide totals for the number of normal hours worked, number of overtime hours worked and total earnings.
- The payslip needs to detail how much was earned for each shift, how many normal, after 6 and overtime hours were worked and what Rate was used for each one.
- The payslip should show any allowances earned for any shift.
