# Project Setup

## Creating user

- create user balakrishna

## Creating database and setting owner

- create database iplproject with owner balakrishna

## Creating tables in iplproject database

- create table matches (
	id integer primary key,
	season integer,
	city text,
	date date,
	team1 text,
	team2 text,
	toss_winner text,
	toss_decision text,
	result text,
	dl_applied integer,
	winner text,
	win_by_runs integer,
	win_by_wickets integer,
	player_of_match text,
	venue text,
	umpire1 text,
	umpire2 text,
    umpire3 text
);

- create table deliveries (
	match_id integer references matches(id),
	inning integer,
	batting_team text,
	bowling_team text,
	over integer,
	ball integer,
	batsman text,
	non_striker text,
	bowler text,
	is_super_over integer,
    wide_runs integer,
    bye_runs integer,
    legbye_runs integer,
    noball_runs integer,
    penalty_runs integer,
    batsman_runs integer,
    extra_runs integer,
    total_runs integer,
    player_dismissed text,
    dismissal_kind text,
    fielder text
);

## Importing data from csv files

- In pgadmin 4 go to
- servers -> PostgreSQL Local -> Databases -> ipldatabase -> Schemas -> Tables -> matches

- right click on the matches table, click import data, Dailog box opens, then select the appropriate options to import csv data

- similarly do for deliveries table