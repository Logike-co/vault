
SQLite format 3

CREATE TABLE tree_nodes
(
	node_id integer primary key,
	parent integer,
	type text,
	name text,
	diagram_id integer
)
CREATE TABLE diagram_info
(
	diagram_id integer,
	name text,
	value text,
	primary key (diagram_id, name)
)
CREATE TABLE items
(
	item_id integer primary key,
	diagram_id integer,
	type text,
	text text,
	selected integer,
	x integer,
	y integer,
	w integer,
	h integer,
	a integer,
	b integer,
	aux_value integer,
	color text,
	format text,
	text2 text
)
CREATE TABLE state
(
	row integer primary key,
	current_dia integer,
	description text
)
CREATE TABLE diagrams
(
	diagram_id integer primary key,
	name text unique,
	origin text,
	description text,
	zoom double
)
CREATE TABLE info
		(
			key text primary key,
			value text
		)'
