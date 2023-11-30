# DDL 2 Go Struct

This is a simple tool to convert the DDL instructions to a struct in Golang using the SQL package.

Note: forked from [Wandecilenio/DDL2GS](https://github.com/Wandecilenio/DDL2GS) and adapted specificly to OracleDB (19c) db-dialect, i.e. Redwood (work-in-progress).

The steps is simple.

First select the ddl create table instructions, example:
```sql
CREATE TABLE public.t_customer
(
  id serial NOT NULL PRIMARY KEY,
  name character varying(255) NOT NULL,
  document character varying(20) NOT NULL,
  created_at timestamp(0) without time zone NOT NULL DEFAULT now(),
  updated_at timestamp(0) without time zone
);
```

Then type `CTRL+SHIFT+p`

And run the `DDL2GS: Convert the DDL instructions to Go Struct` to convert the sql text selected to go struct

Or just select it and press `CTRL+SHIFT+i`

Will result in:

```go
// Customer --
type Customer struct {
	ID	int64	`db:"id"`
	Name	string	`db:"name"`
	Document	string	`db:"document"`
	CreatedAT	*time.Time	`db:"created_at"`
	UpdatedAT	*time.Time	`db:"updated_at"`
}
```
