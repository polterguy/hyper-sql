## Introduction to Hyper SQL

Hyper SQL is a web based alternative to MySQL Workbench, that allows you to easily and securely
administrate your MySQL database. It allows you to execute SQL towards your MySQL databases, as
configured through your _"web.config"_. Below is a screenshot of it.

https://phosphorusfive.files.wordpress.com/2018/05/hyper-sql-screenshot.png

It is consciously centered and architected around SQL as a language, allowing you to save and load
snippets for later references, and such build a library of SQL snippets performing common tasks.
In such a way, it is also an excellent learning tool for learning SQL, allowing you to test
ideas in a highly visual manner, and store your (best) ideas for later. It features syntax
highlighting and AutoCompletion for MySQL syntax, allowing you to click _Ctrl+Space_
(_Cmd+Space on OS X_) to have a dropdown appear, suggesting keywords, table names, and column names
for you automatically.

### Toolbar buttons

* The _"eye"_ toolbar button allows you to rapidly create a _"select * from active table"_ SQL, and
display its result. Notice, this will remove any existing SQL you have in your editor, and the button
is only enabled if you have actually chosen a _"table"_ item, directly or indirectly in your _"database explorer"_ - Which is the tree
view to the left in your page.
* The _"play"_ button will execute your current SQL from your editor, and if possible, create a datagrid
displaying your SQL's result. This button will execute your SQL towards your currently selected database
selector, which is the dropdown select list to the left of it.
* The _"refresh"_ button will refresh your currently active tree view node in your database explorer,
and is useful if you have changed your database/table schema somehow - Or created a new database.
* The _"folder"_ button allows you to load a previously saved SQL snippet.
* The _"floppy disk"_ button allows you to save your current SQL for later references.
* The _"cogs"_ buttons allows you to see the schema for your currently selected database/table.

### Keyboard shortcuts

These keyboard shortcuts are only available when your SQL editor has focus.

* _Ctrl+Space_ (or _Cmd+Space_ on OS X) - Opens up your AutoCompleter
* _Alt+M_ - Maximize your SQL editor.
* _Alt+S_ - Opens up the _"save active SQL"_ window.
* _Alt+L_ - Opens up the _"load SQL snippet"_ window.

### Less is more

Its UX is consciously kept _"minimalistic"_, such that it also should work perfectly on your
phone or tablet, in addition to avoid adding _"cognitive noise"_ to your own ideas. Instead
of trying to do as much as possible, it arguably tries to do as _"little as possible"_, focusing
your attention around SQL as a language. For these reasons it does among other things not contain
_"in-place editing"_ of records or cells, but allows you to easily write your own SQL to perform
such tasks instead. Due to these reasons, it to a much larger extent than other similar tools, forces
you to instead of clicking buttons, actually write SQL to perform the same tasks. However, since
you can store your favorite SQL snippets, this hopefully shouldn't be much of a problem, since this
allows you to build up a library of SQL snippets that you can easily load and execute later.

By default when it creates its result datagrid though, it might not necessarily render your
longtext values correctly. You can click a single row though, to display your values pre formatted
as they are stored in your database. This is chosen to avoid having very long values rendering
pages up and down of text, making it more difficult to scroll and see your data.

I might consider creating _"in-place-editing"_ as a feature in Hyper SQL later, if many users
are requesting this feature.

### Responsive rendering

Hyper SQL renders _"responsively"_, implying it will work perfectly on your phone or tablet, and
automatically resize itself, according to how much screen _"real estate"_ it has available.

### Displaying your data graphically

It contains some few helper functions, that you can actually see in the above screenshot, that allows
you to display your data graphically. For instance, if your result set contains only two columns,
and the second column's values are numbers of some sort - It will suggest automatically creating
a Pie Chart or a Column Chart displaying your data. If you for instance click the above Pie Chart button,
a modal window will display your data in a pie chart. Below is a screenshot of how this will look like.

https://phosphorusfive.files.wordpress.com/2018/05/hyper-sql-pie-chart-screenshot.png

This allows you to easily create visual representations of your data, either using Pie Charts or
Column Charts to visually represent your data.

**Notice**, Hyper SQL will only suggest displaying a chart for you, if you have 40 or less records
in your result set, and your result set contains numbers of some sort in its _second_ column, and
your result set only contains _two columns_.

### Helper functions

Even though Hyper SQL contains a minimum amount of _"bling"_ and _"super-duper-buttons"_, it contains
some few helper buttons that allows you to do some common tasks. More specifically, it contains
two buttons that allows you to generate a _"create database"_ SQL for you, for your active database -
In addition to a _"create table"_ SQL, that allows you to see what SQL is necessary to re-create your
currently active table. You can also easily extend all three toolbars of Hyper SQL easily, by simply
creating a _"toolbar item"_ Hyperlambda file, and put in in the folder associated with your toolbar.
In fact, all toolbar items in Hyper SQL is loaded dynamically like this.

### Security

Hyper SQL should be highly secure. Among other things, it doesn't even allow you to explicitly
connect to any other database server than the one you have configured in your _"web.config"_ file.
This implies that there are no _"where do we store our passwords"_ problems, since this web.config
file is only readable and directly accessible to a _"root"_ account in your system. In addition,
you can also easily use _"Peeples"_ to control access to Hyper SQL. By default, only a _"root"_ account
has access to Hyper SQL. The above feature allows you to give access to Hyper SQL to users in your
Phosphorus Five installation, that does not have root access to your database, and don't even know
where your database is installed for that matter.

### Creating backups of your database

In recent releases of MySQL, Oracle has turned _OFF_ some features necessarily to easily implement
creating backups of your databases. You can still achieve this, by modifying your MySQL's security
settings, and for instance executing an SQL snippet resembling the following.

```sql
select * from YOUR_TABLE into outfile '/foo/bar.txt'
```

At which point you'll need to edit your `--secure-file-priv` options, or figure out the default
folder that MySQL allows you to _"select into"_ to create file backups. Google is your friend here ...

For the above reasons, I have not found (yet) an intelligent way to implement creating and restoring
backups of your databases. If many users are requesting this, I might consider implementing it at
some time in the future. And since I don't want to teach my users to violate what Oracle perceives
as _"security best practices"_, there is no create backup or restore backup support in Hyper SQL (_yet!_)

