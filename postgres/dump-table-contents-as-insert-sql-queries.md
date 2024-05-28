# Dump table contents as insert sql queries

## Create db

For simple dataabse management on you local machine, I strongly recommed installing [PostgreApp](https://postgresapp.com/)

```
createdb cthulhu -U $USER
```

## Create a users table

```
CREATE TABLE IF NOT EXISTS users (
  id           UUID PRIMARY KEY NOT NULL,
  firstname    TEXT NOT NULL,
  lastname     TEXT NOT NULL,
  created_at   TIMESTAMP WITH TIME ZONE NOT NULL DEFAULT NOW(),
  updated_at   TIMESTAMP WITH TIME ZONE
);
```

## Populate the table

Inserting a couple of users sql here.

## Dump the users table

```
pg_dump \
  -h localhost \
  -p 5432 \
  -U $USER -W \
  --table="users" \
  --data-only \
  --column-inserts \
  cthulhu > users.sql
```

## Example output

```
--
-- PostgreSQL database dump
--

-- Dumped from database version 11.0
-- Dumped by pg_dump version 11.0

SET statement_timeout = 0;
SET lock_timeout = 0;
SET idle_in_transaction_session_timeout = 0;
SET client_encoding = 'UTF8';
SET standard_conforming_strings = on;
SELECT pg_catalog.set_config('search_path', '', false);
SET check_function_bodies = false;
SET client_min_messages = warning;
SET row_security = off;

--
-- Data for Name: users; Type: TABLE DATA; Schema: public; Owner: lulu.cthulhu
--

INSERT INTO public.users (id, firstname, lastname, created_at, updated_at) VALUES ('425db3cc-c587-4076-8c97-1072df7a7906', 'John', 'Doe', '2019-04-19 21:06:53.457559-04', '2019-04-19 21:12:40.926747-04');
INSERT INTO public.users (id, firstname, lastname, created_at, updated_at) VALUES ('22457ef3-e0f7-418d-aa67-6bf6f5a13903', 'Jack', 'Smith', '2019-04-23 21:12:54.791943-04', NULL);
```
