# test Configuration

serverity: warn 

- it would be warn you and continue to build the downstream model

error_if/ warn_if: “>30” 

- only warn/error if the number of failed records >30

where: “order_date> ‘2018-03-01’”

- filter down the failed records based on the expression.

limit: 10

- will only include the first 10 failures