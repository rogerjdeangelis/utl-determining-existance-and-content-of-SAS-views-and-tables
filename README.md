# utl-determining-existance-and-content-of-SAS-views-and-tables
Determining-existance-and-content-of-SAS-views-and-tables
    Determining-existance-and-content-of-SAS-views-and-tables                                                                    
                                                                                                                                 
    This is just a academic post without a solution.                                                                             
    It is not a trivial problem.                                                                                                 
                                                                                                                                 
    Determining the number of rows in a sas table or view is not trivial due to boundary conditions                              
                                                                                                                                 
      Boundary Conditions                                                                                                        
                                                                                                                                 
         1. Table or view does not exist                                                                                         
         2. Table or view exists but  has 0 file size on disk                                                                    
         3. Table or view has some deleted rows                                                                                  
         4. Table or view is empty because all rows have been deleted(has                                                        
         5. One row with 0 columns                                                                                               
         6. Has one or more rows and columns but all columns have missing values(this happens)                                   
                                                                                                                                 
    github                                                                                                                       
    https://tinyurl.com/yxzh8rqp                                                                                                 
    https://github.com/rogerjdeangelis/utl-determining-existance-and-content-of-SAS-views-and-tables                             
                                                                                                                                 
    Some usefull tools                                                                                                           
                                                                                                                                 
     1. SQL outobs=1                                                                                                             
     2. NLOBS point= nobs= end= eof=                                                                                             
     3. data _null_ ;                                                                                                            
        infile "d:/sd1/zroSiz.sas7bdat" end = empty ; * 1 if 0 file size (Paul Dorfman);                                         
           put empty=;                                                                                                           
        run;                                                                                                                     
     4. proc sql; select count * from bigData; quit; * is instantaneous;                                                         
     5. %let dsID = %sysfunc(open(&iDs));                                                                                        
     6. attrn(dsID,nvars)                                                                                                        
     7. attrn(dsID,nlobs)                                                                                                        
                                                                                                                                 
    Related post                                                                                                                 
    gihub                                                                                                                        
    https://github.com/rogerjdeangelis/utl-the-four-types-of-empty-sas-tables                                                    
                                                                                                                                 
    StackOverflow                                                                                                                
    https://tinyurl.com/y4fum42c                                                                                                 
    https://stackoverflow.com/questions/5658994/how-to-detect-how-many-observations-in-a-dataset-or-if-it-is-empty-in-sas        
                                                                                                                                 
                                                                                                                                 
    TYPES OF MISSING TABLEs                                                                                                      
                                                                                                                                 
       1. Completely Empty                                                                                                       
                                                                                                                                 
          Observations          0                                                                                                
          Variables             0                                                                                                
          Indexes               0                                                                                                
          Observation Length    0                                                                                                
          Deleted Observations  0                                                                                                
                                                                                                                                 
       2. Completely Empty except one deleted observation more useful                                                            
          Works in SQL and datastep - allows processing without error                                                            
                                                                                                                                 
          Observations          0                                                                                                
          Variables             1                                                                                                
          Indexes               0                                                                                                
          Observation Length    8                                                                                                
          Deleted Observations  1                                                                                                
                                                                                                                                 
       3. 1 observation 0 variables                                                                                              
                                                                                                                                 
          Observations          1                                                                                                
          Variables             0                                                                                                
          Indexes               0                                                                                                
          Observation Length    0                                                                                                
          Deleted Observations  0                                                                                                
                                                                                                                                 
       4. 1 observation 1 variable with missing value                                                                            
                                                                                                                                 
          Observations          1                                                                                                
          Variables             1                                                                                                
          Indexes               0                                                                                                
          Observation Length    8                                                                                                
          Deleted Observations  0                                                                                                
                                                                                                                                 
       5. Exists but has 0 filesize                                                                                              
                                                                                                                                 
          d:/sd1/zroFylSiz.sas7bdat                                                                                              
                                                                                                                                 
          Name                Date         Type        Size                                                                      
         zroFylSiz.sas7bdat   6/22/2019    sas7bdat     0                                                                        
                                                                                                                                 
                                                                                                                                 
