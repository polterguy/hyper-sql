## Hyper SQL's API

Hyper SQL contains a fairly rich API, allowing you to tap easily into it from any angle  you wish.
Among other things, you can instantiate it as an _"extension widget"_. If you're reading this file
from any other module than Hyper SQL, you can evaluate the snippet below to open up a modal widget, containing Hyper SQL.

```hyperlambda-snippet
/*
 * Creates a modal widget containing Hyper SQL.
 */
p5.web.include-css-file:@HYPER-SQL/media/main.css
create-widgets
  micro.widgets.modal
    class:micro-widgets-modal large
    widgets

      /*
       * Our Hyper SQL "extension widget".
       */
      hyper-sql.widgets.sql
```

### Widget lambda events

When you have Hyper SQL instantiatet somehow on your page, you can use any of the following
_"widget lambda events"_ to automate it, or somehow manipulate its state one way or another.

* __[hyper-sql.is-open]__ - Returns boolean _"true"_ if Hyper SQL is running.
* __[hyper-sql.sql-editor.set-sql]__ - Sets the active SQL in your SQL editor to the specified __[\_arg]__ value.
* __[hyper-sql.sql-editor.get-sql]__ - Returns the active SQL from your SQL editor.
* __[hyper-sql.execute-sql]__ - Executes the specified __[\_arg]__ SQL towards your currently active database, and creates a datagrid with the results, if any.
* __[hyper-sql.database.get]__ - Returns the active database back to caller. This is the database that
is currently selected in your _"database selector"_ - Implying the _"dropdown select"_ widget at the top of your page.

In addition to the above lambda events, Hyper SQL will also _"publish"_ events, when some specific action
is occurring within it. You can tap into these events yourself if you wish. These events are as follows.

* __[hyper-sql.database-explorer.selected-item-changed]__ - Invoked when the active item in your database explorer (tree view) has changed for some reasons.
* __[hyper-sql.active-database.changed]__ - Invoked when the active database is somehow changed.
* __[hyper-sql.sql.executed]__ - Invoked when some SQL is actually executed towards your database, but before a resulting datagrid is created.
