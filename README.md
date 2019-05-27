## DSNACCOX
- The DB2® real-time statistics stored procedure (DSNACCOX) is a sample stored procedure that makes recommendations to help you maintain your DB2 databases.
- Read more about [DSNACCOX](https://www.ibm.com/support/knowledgecenter/SSEPEK_10.0.0/sqlref/src/tpc/db2z_sp_dsnaccox.html)
- Codes provided are written in REXX Language.



## Limitations:
- CHECKLVL Parameter is set to 0 . So Exception Tables will not be used as of now.
- SPECIALPARM parameter is set to null .Will not be used. 
- Codes provided are developed and tested on z/OS 2.3 ,DB2 V10 .

## Install Instructions:
- Option 1
  - Upload JCL and REXX Code to PDS dataset . 
  - Dataset Attributes LRECL=80,RECFM=FB.
  - Make sure while uploading format of the file does not change at destination.
  - READ JCL instructions to customise it further.
- Option 2
  - Upload "dsnaccox.xmit" file in binary format on mainframe .
  - Dataset attribute should be FB,LRECL=80
  - RECEIVE XMIT FILE using command **receive indsname('hlq.dsnaccox.xmit')**.
  Press enter to ignore messages.Output dataset should **hlq.dsnaccox** with following members DSNACCOX and JCLCCOX.

## How to Use ?
- Customise JCLCCOX as per JCL Instructions.
- Submit JCLCCOX to get the DSNACCOX recommendations
- Output messages (recommendations) are displayed in RECOMMND ddname.
- Parameters used by DSNACCOX stored procedure are displayed in PARMUSED ddname.
- To override stored procedure parameters use **//PARMOVRD DD** 
  - Parameters that can be override and default values used are:
    - CRUpdatedPagesPct :20 
    - CRUpdatedPagesABS :0  
    - CRChangesPct :10      
    - CRDaySncLastCopy :2   
    - ICRUpdatedPagesPct :1 
    - ICRUpdatedPagesAbs :0 
    - ICRChangesPct :1      
    - CRIndexSize   :50     
    - RRTInsertsPct :25         
    - RRTInsertsAbs :0        
    - RRTDeletesPct :25     
    - RRTDeletesAbs :0      
    - RRTUnclustInsPct :10  
    - RRTDisorgLOBPct  :50  
    - RRTDataSpaceRat  :2   
    - RRTMassDelLimit  :0   
    - RRTIndRefLimit   :5   
    - RRIInsertsPct   :30   
    - RRIInsertsAbs   :0    
    - RRIDeletesPct   :30   
    - RRIDELETESABS   :0    
    - RRIAppendInsertPct :30
    - RRIPseudoDeletePct :5 
    - RRIMassDelLimit :0    
    - RRILeafLimit :10      
    - RRINumLevelsLimit :0  
    - SRTInsDelUpdPct   :20 
    - SRTInsDelUpdAbs   :0  
    - SRTMassDelLimit   :0  
    - SRIInsDelPct      :20 
    - SRIInsDelAbs   :0     
    - SRIMassDelLimit   :0  
    - ExtentLimit       :254
- Following SYSIN Parameters should have a value assigned to it else unexpected results.
  - DB2SSID =DBU1        
  - QUERYTYPE =ALL       
  - OBJTYPE =TS          
  - ICTYPE =F            
  - CATSCHEMA =SYSIBM    
  - LOCALSCHEMA =DSNACC  
  - CRITERIA = DB        
  - NAME = DSN8DKAS      
