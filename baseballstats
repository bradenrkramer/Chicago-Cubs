CREATE DATABASE baseball

CREATE TABLE public.basestats
(
    rank integer NOT NULL,
    year integer,
    team character varying(50) COLLATE pg_catalog."default",
    wins integer,
    losses integer,
    win_loss_percent numeric,
    CONSTRAINT basestats_pkey PRIMARY KEY (rank)
)

CREATE TABLE public.batstats
(
    rank integer NOT NULL,
    baseonballs integer,
    strikeouts integer,
    average numeric,
    sacrificehits integer,
    sacrificefly integer,
    CONSTRAINT batstats_pkey PRIMARY KEY (rank)
)

CREATE TABLE public.extrabasestats
(
    rank integer,
    runs integer,
    hits integer,
    doubles integer,
    triples integer,
    homeruns integer,
    rbi integer,
    CONSTRAINT extrabasestats_rank_fkey FOREIGN KEY (rank)
        REFERENCES public.basestats (rank) MATCH SIMPLE
        ON UPDATE NO ACTION
        ON DELETE NO ACTION
)

CREATE TABLE public.innings
(
    inning integer,
    aheadwins integer,
    aheadlosses integer,
    aheadpercent numeric,
    tiedwins integer,
    tiedlosses integer,
    tiedpercent numeric,
    behindwins integer,
    behindlosses integer,
    behindpercent numeric
)

CREATE TABLE public.stealingstats
(
    rank integer,
    stolenbases integer,
    caughtsteal integer,
    CONSTRAINT stealingstats_rank_fkey FOREIGN KEY (rank)
        REFERENCES public.basestats (rank) MATCH SIMPLE
        ON UPDATE NO ACTION
        ON DELETE NO ACTION
)

CREATE TABLE public.teambatstats
(
    rank integer,
    numberplayersbat integer,
    runspergame numeric,
    plateappearances integer,
    CONSTRAINT teambatstats_rank_fkey FOREIGN KEY (rank)
        REFERENCES public.basestats (rank) MATCH SIMPLE
        ON UPDATE NO ACTION
        ON DELETE NO ACTION
)


select basestats.rank, year, team, win_loss_percent, extrabasestats.doubles
	from basestats
join extrabasestats
	on basestats.rank = extrabasestats.rank
  
select basestats.rank, year, team, win_loss_percent, extrabasestats.doubles,
	extrabasestats.triples, extrabasestats.homeruns
	from basestats
join extrabasestats
	on basestats.rank = extrabasestats.rank

select basestats.rank, year, team, win_loss_percent,
	stealingstats.stolenbases, stealingstats.caughtsteal
	from basestats
join stealingstats
	on basestats.rank = stealingstats.rank
  
select basestats.rank, year, team, win_loss_percent,
	batstats.baseonballs, batstats.strikeouts, batstats.sacrificehits
	from basestats
join batstats
	on basestats.rank = batstats.rank

select basestats.rank, year, team, win_loss_percent,
	batstats.baseonballs, batstats.sacrificehits,
	teambatstats.runspergame
	from basestats
join batstats
	on basestats.rank = batstats.rank
join teambatstats
	on batstats.rank = teambatstats.rank

select basestats.rank, year, team, win_loss_percent,
	batstats.baseonballs, extrabasestats.homeruns
	from basestats
join batstats
	on basestats.rank = batstats.rank
join extrabasestats
	on batstats.rank = extrabasestats.rank

select basestats.rank, year, team, win_loss_percent,
	batstats.baseonballs, batstats.strikeouts, extrabasestats.homeruns
	from basestats
join batstats
	on basestats.rank = batstats.rank
join extrabasestats
	on batstats.rank = extrabasestats.rank

select basestats.rank, year, team, win_loss_percent,
	extrabasestats.doubles, extrabasestats.triples, extrabasestats.homeruns
	from basestats
join extrabasestats
	on basestats.rank = extrabasestats.rank

select basestats.rank, year, team, win_loss_percent,
	extrabasestats.doubles, extrabasestats.triples, extrabasestats.homeruns
	from basestats
join extrabasestats
	on basestats.rank = extrabasestats.rank
where win_loss_percent > 0.5

select basestats.rank, year, team, win_loss_percent,
	extrabasestats.doubles, extrabasestats.triples, extrabasestats.homeruns
	from basestats
join extrabasestats
	on basestats.rank = extrabasestats.rank
where win_loss_percent < 0.5

select basestats.rank, year, team, win_loss_percent,
	batstats.strikeouts, extrabasestats.homeruns
	from basestats
join extrabasestats
	on basestats.rank = extrabasestats.rank
join batstats
	on extrabasestats.rank = batstats.rank
  
