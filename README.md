# sql
记录sql语句
select mandt,id,mast_matnr,mast_werks from (select mandt,id,mast_matnr,mast_werks FROM (VALUES ('100','5655CDS','5655CD3','1701'),('100','5655CDS','5655CD3','1702')) dm(mandt,id,mast_matnr,mast_werks))

SELECT zsession ,mandt,create_time,text,text_type from (select timestampdiff(16,char(timestamp('2016-06-07')-timestamp('2015-04-06'))) > '365' as a, zsession,mandt,create_time,text,text_type from sapr3.zdm_logdtl)

 select 'rdh' source,rdh.*  from RDHAUDIT.RDH_MATERIAL as rdh
 inner join RDHAUDIT.CBS_MATERIAL as cbs on rdh.mara_matnr=cbs.mara_matnr and rdh.mvke_vkorg=cbs.mvke_vkorg
 inner join RDHAUDIT.IERP_MATERIAL as ierp on rdh.mara_matnr=ierp.mara_matnr and rdh.mvke_vkorg=ierp.mvke_vkorg
 where  (rdh.mara_matnr,rdh.mvke_vkorg) not in
 (
 select rdh.mara_matnr,rdh.mvke_vkorg from RDHAUDIT.RDH_MATERIAL as rdh
 inner join RDHAUDIT.CBS_MATERIAL as cbs 
 on  rdh.mara_matnr=cbs.mara_matnr and rdh.mvke_vkorg=cbs.mvke_vkorg
 and rdh.MARA_MTART=cbs.MARA_MTART and rdh.MVKE_VTWEG=cbs.MVKE_VTWEG
 and rdh.MVKE_VERSG=cbs.MVKE_VERSG and rdh.MVKE_SKTOF=cbs.MVKE_SKTOF 
 and rdh.MVKE_VMSTA=cbs.MVKE_VMSTA and rdh.MVKE_VMSTD=cbs.MVKE_VMSTD 
 and rdh.MVKE_AUMNG=cbs.MVKE_AUMNG and rdh.MVKE_MTPOS=cbs.MVKE_MTPOS
 and rdh.MVKE_DWERK=cbs.MVKE_DWERK and rdh.MVKE_PRODH=cbs.MVKE_PRODH 
 and rdh.MVKE_KTGRM=cbs.MVKE_KTGRM and rdh.MVKE_MVGR1=cbs.MVKE_MVGR1
 and rdh.MVKE_MVGR2=cbs.MVKE_MVGR2 and rdh.MVKE_MVGR3=cbs.MVKE_MVGR3
 inner join RDHAUDIT.IERP_MATERIAL as ierp 
 on  rdh.mara_matnr=ierp.mara_matnr and rdh.mvke_vkorg=ierp.mvke_vkorg
 and rdh.MARA_MTART=ierp.MARA_MTART and rdh.MVKE_VTWEG=ierp.MVKE_VTWEG
 and rdh.MVKE_VERSG=ierp.MVKE_VERSG and rdh.MVKE_SKTOF=ierp.MVKE_SKTOF 
 and rdh.MVKE_VMSTA=ierp.MVKE_VMSTA and rdh.MVKE_VMSTD=ierp.MVKE_VMSTD 
 and rdh.MVKE_AUMNG=ierp.MVKE_AUMNG and rdh.MVKE_MTPOS=ierp.MVKE_MTPOS
 and rdh.MVKE_DWERK=ierp.MVKE_DWERK and rdh.MVKE_PRODH=ierp.MVKE_PRODH 
 and rdh.MVKE_KTGRM=ierp.MVKE_KTGRM and rdh.MVKE_MVGR1=ierp.MVKE_MVGR1
 and rdh.MVKE_MVGR2=ierp.MVKE_MVGR2 and rdh.MVKE_MVGR3=ierp.MVKE_MVGR3
 ) and rdh.mara_mtart='ZSWO'
 union 
 select 'cbs' source,cbs.*  from RDHAUDIT.RDH_MATERIAL as cbs
 inner join RDHAUDIT.rdh_MATERIAL as rdh on rdh.mara_matnr=cbs.mara_matnr and rdh.mvke_vkorg=cbs.mvke_vkorg
 inner join RDHAUDIT.IERP_MATERIAL as ierp on rdh.mara_matnr=ierp.mara_matnr and rdh.mvke_vkorg=ierp.mvke_vkorg
 where  (cbs.mara_matnr,cbs.mvke_vkorg) not in
 (
 select rdh.mara_matnr,rdh.mvke_vkorg from RDHAUDIT.RDH_MATERIAL as rdh
 inner join RDHAUDIT.CBS_MATERIAL as cbs 
 on  rdh.mara_matnr=cbs.mara_matnr and rdh.mvke_vkorg=cbs.mvke_vkorg
 and rdh.MARA_MTART=cbs.MARA_MTART and rdh.MVKE_VTWEG=cbs.MVKE_VTWEG
 and rdh.MVKE_VERSG=cbs.MVKE_VERSG and rdh.MVKE_SKTOF=cbs.MVKE_SKTOF 
 and rdh.MVKE_VMSTA=cbs.MVKE_VMSTA and rdh.MVKE_VMSTD=cbs.MVKE_VMSTD 
 and rdh.MVKE_AUMNG=cbs.MVKE_AUMNG and rdh.MVKE_MTPOS=cbs.MVKE_MTPOS
 and rdh.MVKE_DWERK=cbs.MVKE_DWERK and rdh.MVKE_PRODH=cbs.MVKE_PRODH 
 and rdh.MVKE_KTGRM=cbs.MVKE_KTGRM and rdh.MVKE_MVGR1=cbs.MVKE_MVGR1
 and rdh.MVKE_MVGR2=cbs.MVKE_MVGR2 and rdh.MVKE_MVGR3=cbs.MVKE_MVGR3
 inner join RDHAUDIT.IERP_MATERIAL as ierp 
 on  rdh.mara_matnr=ierp.mara_matnr and rdh.mvke_vkorg=ierp.mvke_vkorg
 and rdh.MARA_MTART=ierp.MARA_MTART and rdh.MVKE_VTWEG=ierp.MVKE_VTWEG
 and rdh.MVKE_VERSG=ierp.MVKE_VERSG and rdh.MVKE_SKTOF=ierp.MVKE_SKTOF 
 and rdh.MVKE_VMSTA=ierp.MVKE_VMSTA and rdh.MVKE_VMSTD=ierp.MVKE_VMSTD 
 and rdh.MVKE_AUMNG=ierp.MVKE_AUMNG and rdh.MVKE_MTPOS=ierp.MVKE_MTPOS
 and rdh.MVKE_DWERK=ierp.MVKE_DWERK and rdh.MVKE_PRODH=ierp.MVKE_PRODH 
 and rdh.MVKE_KTGRM=ierp.MVKE_KTGRM and rdh.MVKE_MVGR1=ierp.MVKE_MVGR1
 and rdh.MVKE_MVGR2=ierp.MVKE_MVGR2 and rdh.MVKE_MVGR3=ierp.MVKE_MVGR3
 ) and rdh.mara_mtart='ZSWO'
 union 
 select 'ierp' source,ierp.*  from RDHAUDIT.RDH_MATERIAL as ierp
 inner join RDHAUDIT.rdh_MATERIAL as rdh on rdh.mara_matnr=ierp.mara_matnr and rdh.mvke_vkorg=ierp.mvke_vkorg
 inner join RDHAUDIT.cbs_MATERIAL as cbs on cbs.mara_matnr=ierp.mara_matnr and cbs.mvke_vkorg=ierp.mvke_vkorg
 where  (ierp.mara_matnr,ierp.mvke_vkorg) not in
 (
 select rdh.mara_matnr,rdh.mvke_vkorg from RDHAUDIT.RDH_MATERIAL as rdh
 inner join RDHAUDIT.CBS_MATERIAL as cbs 
 on  rdh.mara_matnr=cbs.mara_matnr and rdh.mvke_vkorg=cbs.mvke_vkorg
 and rdh.MARA_MTART=cbs.MARA_MTART and rdh.MVKE_VTWEG=cbs.MVKE_VTWEG
 and rdh.MVKE_VERSG=cbs.MVKE_VERSG and rdh.MVKE_SKTOF=cbs.MVKE_SKTOF 
 and rdh.MVKE_VMSTA=cbs.MVKE_VMSTA and rdh.MVKE_VMSTD=cbs.MVKE_VMSTD 
 and rdh.MVKE_AUMNG=cbs.MVKE_AUMNG and rdh.MVKE_MTPOS=cbs.MVKE_MTPOS
 and rdh.MVKE_DWERK=cbs.MVKE_DWERK and rdh.MVKE_PRODH=cbs.MVKE_PRODH 
 and rdh.MVKE_KTGRM=cbs.MVKE_KTGRM and rdh.MVKE_MVGR1=cbs.MVKE_MVGR1
 and rdh.MVKE_MVGR2=cbs.MVKE_MVGR2 and rdh.MVKE_MVGR3=cbs.MVKE_MVGR3
 inner join RDHAUDIT.IERP_MATERIAL as ierp 
 on  rdh.mara_matnr=ierp.mara_matnr and rdh.mvke_vkorg=ierp.mvke_vkorg
 and rdh.MARA_MTART=ierp.MARA_MTART and rdh.MVKE_VTWEG=ierp.MVKE_VTWEG
 and rdh.MVKE_VERSG=ierp.MVKE_VERSG and rdh.MVKE_SKTOF=ierp.MVKE_SKTOF 
 and rdh.MVKE_VMSTA=ierp.MVKE_VMSTA and rdh.MVKE_VMSTD=ierp.MVKE_VMSTD 
 and rdh.MVKE_AUMNG=ierp.MVKE_AUMNG and rdh.MVKE_MTPOS=ierp.MVKE_MTPOS
 and rdh.MVKE_DWERK=ierp.MVKE_DWERK and rdh.MVKE_PRODH=ierp.MVKE_PRODH 
 and rdh.MVKE_KTGRM=ierp.MVKE_KTGRM and rdh.MVKE_MVGR1=ierp.MVKE_MVGR1
 and rdh.MVKE_MVGR2=ierp.MVKE_MVGR2 and rdh.MVKE_MVGR3=ierp.MVKE_MVGR3
 ) and rdh.mara_mtart='ZSWO'
 
 with ur
 
 select distinct zdmlogsys from(select row_number() over(order by mandt) as tt,tab.* from(select mandt,zdmmsgtyp,zdmobjtyp,zdmobjkey,zdm_change_num,tabname,'R' as zdm_status,zdm_change_type,zdm_req_priority,zdm_broadcast,zdm_source,zdmlogsys
from SAPR3.zdm_parktable
WHERE ZDMCLASS='MD_BH_ALL' and MANDT='100' and ZDM_CREATE_DATE>='20190101' and ZDM_CREATE_DATE<='20191231' with ur)tab
)where tt between 1 and 20 with ur
