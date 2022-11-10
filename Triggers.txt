delimiter $$
CREATE TRIGGER tg1
BEFORE INSERT ON student
for each row
begin
set new.name=upper(new.name);
set new.city=upper(new.city);
end;
$$


-----------------------------

delimiter $$
CREATE TRIGGER tg2
AFTER UPDATE ON person
for each row
begin
insert INTO audit_log
VALUES(old.fname,old.lname,new.fname,new.lname,curdate() );
end;
$$
