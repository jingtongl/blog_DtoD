添加学员语句：
insert into crm_students
 (name,sex,birthday,teaching_methods,par_phone,par_name,guardian_phone,province,city,district,campus,addr,datasource_id,extra_ds_edit,stu_label,extra_level ) 
values
 ( '测试数据库','1','20170403','1','13388888888','测试','13388888888','上海市','上海市','黄浦区','1','测试地址','134','1','1','1' );

查询学员是否被删除语句：
select delete_time from crm_students where par_phone = '13388888885';

添加学员乐器：（乐器常用的course_id：1钢琴，2小提琴；是否具有乐器instrument：0没有，1有）
insert into crm_stu_purpose (sid,course_id,instrument) VALUES
((select id from crm_students where par_phone = '13388888888' and delete_time is null),'2','1');

查询学员乐器信息
select * from crm_stu_purpose where  sid =(select id from crm_students where par_phone = '13388888888' and delete_time is null);

查询乐器信息：
select * from crm_opt_course;

查询到数据库存在该条数据，并且没有别删除
select id from crm_students where par_phone = '13388888888' and delete_time is null;


查询销售信息：李井通ID ：673
select * from tm_admin where id=673;
select * from tm_admin where  real_name='李井通' and delete_time is null;

给学员添加销售：
select unix_timestamp(now());
update crm_stu_purpose  set pid =673,leads_no = (select unix_timestamp(now())) where sid =(select id from crm_students where par_phone = '13388888888' and delete_time is null);

新建教师：
insert into tm_teacher (audit,audit_status,personal_status,identity_status,education_status,settlement_status,is_black,recommend,name,sex,tel,birthYear,school,faculty,signed,source) 
VALUES ('2','9','2','2','2','2','1','2','测试教师','1','13255555555','1990',' 学校','学院','2','1');

查询来源
select count(id) from crm_datasource where ID ='344' ;

查询学员信息
select * from crm_students where name like '%测试%' and delete_time is null;