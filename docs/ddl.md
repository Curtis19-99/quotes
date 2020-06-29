## Data Definition Language (DDL)

```sqlite
create table if not exists `Source`
(
    `source_id` integer primary key autoincrement not null,
    `name`      text                              not null collate NOCASE
);

create unique index if not exists `index_Source_name` on `Source` (`name`);

create table if not exists `Quote`
(
    `quote_id`  integer primary key autoincrement not null,
    `source_id` integer,
    `text`      text                              not null collate NOCASE,
    foreign key (`source_id`) references `Source` (`source_id`) on update no action on delete set null
);

create index if not exists `index_Quote_source_id` on `Quote` (`source_id`);
```

[`ddl.sql`](sql/ddl.sql)