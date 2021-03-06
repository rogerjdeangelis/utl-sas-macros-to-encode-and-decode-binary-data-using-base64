# utl-sas-macros-to-encode-and-decode-binary-data-using-base64
SAS macros to=encode and decode binary data using base64 

    SAS macros to=encode and decode binary data using base64                                                         
                                                                                                                     
      Two algorithms (macros)                                                                                        
                                                                                                                     
           1. utl_encodeBase64.sas - base64 encode of binary file                                                    
              %utl_encodeBase64(inp=d:/xls/class.xlsx,out=d:/txt/class_encode.txt);                                  
                                                                                                                     
           2. utl_decodeBase64.sas - base64 decode of base64 encoded file                                            
              %utl_decodeBase64(inp=d:/txt/class_encode.txt,out=d:/xls/class_decode.xlsx);                           
                                                                                                                     
    SAS drops down to Python to do the encode decode                                                                 
    Check Python doc for options and safe modes                                                                      
                                                                                                                     
    Problem: Base64 enode and decode an excel workbook file                                                          
                                                                                                                     
    Use macro utlrulr to display binary data in hex                                                                  
                                                                                                                     
    macros utlrulr, utl_encodeBase64 and utldecodeBase64  (alson on the end of thos message;                         
    https://tinyurl.com/y9nfugth                                                                                     
    https://github.com/rogerjdeangelis/utl-macros-used-in-many-of-rogerjdeangelis-repositories                       
                                                                                                                     
    *                         _                                                                                      
      ___ _ __   ___ ___   __| | ___                                                                                 
     / _ \ '_ \ / __/ _ \ / _` |/ _ \                                                                                
    |  __/ | | | (_| (_) | (_| |  __/                                                                                
     \___|_| |_|\___\___/ \__,_|\___|                                                                                
     _                   _                                                                                           
    (_)_ __  _ __  _   _| |_                                                                                         
    | | '_ \| '_ \| | | | __|                                                                                        
    | | | | | |_) | |_| | |_                                                                                         
    |_|_| |_| .__/ \__,_|\__|                                                                                        
            |_|                                                                                                      
    ;                                                                                                                
                                                                                                                     
    * Make binary excel workbook;                                                                                    
                                                                                                                     
    libname xel "d:/xls/class.xlsx";                                                                                 
    data xel.class;                                                                                                  
      set sashelp.class;                                                                                             
    run;quit;                                                                                                        
    libname xel clear;                                                                                               
                                                                                                                     
    Here is what a excel workbook looks like in binary                                                               
                                                                                                                     
    d:/xls/class.xlsx                                                                                                
    =================                                                                                                
                                                                                                                     
    %utlrulr(                                                                                                        
      uinflt=d:/xls/class.xlsx                                                                                       
     ,uotflt=d:/txt/classHex.txt                                                                                     
     ,ulrecl  =100                                                                                                   
     ,uprnlen =100                                                                                                   
     ,urecfm=F                                                                                                       
     ,uobs=6                                                                                                         
    );                                                                                                               
                                                                                                                     
    ASCII Flatfile Ruler & Hex                                                                                       
    utlrulr                                                                                                          
    d:/xls/class.xlsx                                                                                                
    d:/txt/classHex.txt                                                                                              
                                                                                                                     
                                                                                                                     
     --- Record Number ---  1   ---  Record Length ---- 100                                                          
                                                                                                                     
    PK.........cCNA."9l...........[Content_Types].xml...N.0.E.H...-J..@.%t.c..(.`.I../.nI..I.*T.&.n.$...             
    1...5....10...15...20...25...30...35...40...45...50...55...60...65...70...75...80...85...90...95...1             
    5400100000964441236000A00010005466766755776752766A9C4C314F4F8E24DB4027C609216E4ED2D64F9482592D6E2FBF             
    0B34400880733E1729C10025003000B3FE45E4F49053DE8DCD4BE300578C35DAC2085413958F0C936F9E9FE9AA4560E24697             
                                                                                                                     
                                                                                                                     
     --- Record Number ---  2   ---  Record Length ---- 100                                                          
                                                                                                                     
    Z.O1i.&k.Q9[.q>...pR.yI.g..-%1q+.v.J..H'....l.!..m,i...c,......`q.r....a.<.K>.v=..0.l....jPT#...."(.             
    1...5....10...15...20...25...30...35...40...45...50...55...60...65...70...75...80...85...90...95...1             
    514368260535D73A0A75D74D6CD22372B714B842F91C6E21A62699B628108BF67A7CF896C31430731D3E609BD655281A9220             
    AEF19C6B819B21E24C02999F7F9D511B966AA1877775C3124DC9D2F3CAACF930162104F1EC7BE76DAD01C2B24A04344F8289             
                                                                                                                     
                                                                                                                     
     --- Record Number ---  3   ---  Record Length ---- 100                                                          
                                                                                                                     
    d.Cz...X.....X....a..2%.[.6EI..Z..p.lm.....J..N.."y.......w.W...........17\.!!b.h........y.......S..             
    1...5....10...15...20...25...30...35...40...45...50...55...60...65...70...75...80...85...90...95...1             
    6C47E0C5ADA0C50ACB69A32058344BF5097066E97EA4094A027F0BEC8C7F5A2E0FEDFC1B335D226D68E8D80BA70F909CD5FD             
    4A3A16D8397BB8348A1C325FB965997A9E0FCD5EF6AA90ECC29418C4CE7A7DEBF31C2C9A17C9112A887E09E2F909626893C4             
                                                                                                                     
                                                                                                                     
     --- Record Number ---  4   ---  Record Length ---- 100                                                          
                                                                                                                     
    ..&a...yzat2...|.....O...I.2.(.!..g.. \..'...yK.f..._.D..x...@...!......6.......`e...d......A....[..             
    1...5....10...15...20...25...30...35...40...45...50...55...60...65...70...75...80...85...90...95...1             
    1126CCF77673BAB71980C4B80403F202A06B0258B2FB874F6F015E49D7DD14CF12DA8BFB3CBD08AF66DAD6EC1DDF4BF705FC             
    E2611169A142DE8CACFC5F64699238919170B0C0F78E99BF6B85F94EA8B6007F919D952D6773339605A634DC10B910DF4B83             
                                                                                                                     
                                                                                                                     
     --- Record Number ---  5   ---  Record Length ---- 100                                                          
                                                                                                                     
    ..C..=`....o_PK.........cCNn..G............xl/worksheets/sheet1.xml..]s.8...wf...}..?bg.t..M;..v6...             
    1...5....10...15...20...25...30...35...40...45...50...55...60...65...70...75...80...85...90...95...1             
    DC40036CBF865540010000096446DF4F000C100100076276767666772766673276699579318E76F0C7C836697E143DE73EEB             
    823F7D01AEAFF0B34400880733EE177D4007A0080008CF7F2B385543F385541E8DCD9D3B846F76F33D37F27C4A8DB3E66DE5             
                                                                                                                     
                                                                                                                     
     --- Record Number ---  6   ---  Record Length ---- 100                                                          
                                                                                                                     
    .... F.I._.. ...s.+.8~....8#V......d.Ey.G....2../.........jE....d......7...z...>0.<.P...A..*.....Z_.             
    1...5....10...15...20...25...30...35...40...45...50...55...60...65...70...75...80...85...90...95...1             
    0BA024C495B920E87928379F10325171BFC6C47E41AEB3112FDFC1ECCF64C8EA6DF1AF837FB71FB33A3A5DDF4AE20EFC0558             
    C2D906893FF204B03AB38EF3E9836FF59704D59D771F1259F77EFF4327A5BC6247E3BDF7FE1A42EE06CD067E19AA8A40AAF8             
                                                                                                                     
    *                         _                                                                                      
      ___ _ __   ___ ___   __| | ___                                                                                 
     / _ \ '_ \ / __/ _ \ / _` |/ _ \                                                                                
    |  __/ | | | (_| (_) | (_| |  __/                                                                                
     \___|_| |_|\___\___/ \__,_|\___|                                                                                
                 _               _                                                                                   
      ___  _   _| |_ _ __  _   _| |_                                                                                 
     / _ \| | | | __| '_ \| | | | __|                                                                                
    | (_) | |_| | |_| |_) | |_| | |_                                                                                 
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                
                    |_|                                                                                              
    ;                                                                                                                
                                                                                                                     
    %utlrulr(                                                                                                        
      uinflt=d:/txt/class_encode.txt                                                                                 
     ,uotflt=d:/txt/class_encodeBase64.txt                                                                           
     ,ulrecl  =100                                                                                                   
     ,uprnlen =100                                                                                                   
     ,urecfm=F                                                                                                       
     ,uobs=6                                                                                                         
    );                                                                                                               
                                                                                                                     
    * Note only characters A-Z, a-z, / and + are used;                                                               
                                                                                                                     
    ASCII Flatfile Ruler & Hex                                                                                       
    utlrulr                                                                                                          
    d:/txt/class_encode.txt                                                                                          
    d:/txt/class_encodeBase64.txt                                                                                    
                                                                                                                     
                                                                                                                     
     --- Record Number ---  1   ---  Record Length ---- 100                                                          
                                                                                                                     
    UEsDBBQAAAgIAJdjQ05BFyI5bAEAAKIFAAATAAAAW0NvbnRlbnRfVHlwZXNdLnhtbK2Uy07DMBBF90j8g+UtStyyQAgldMFjCZUo             
    1...5....10...15...20...25...30...35...40...45...50...55...60...65...70...75...80...85...90...95...1             
    5474445444644466533447436444444444454444534766566656546755464667643573344444336362575777546664464556             
    5534221111791A4A1052699521511B961114111170E62E2C2E2668C7A8E4CE842B259074D22690A87B543499117C4D6A3A5F             
                                                                                                                     
                                                                                                                     
     --- Record Number ---  2   ---  Record Length ---- 100                                                          
                                                                                                                     
    H2DsSePWL9luSf+eSYoqVJUm0G7iJPa591oeTzFpjCZrCFE5W9JxPqIErHBS2XlJ32fP2S0lMXEruXYWSrqBSCf3lxfFbOMhEqRt             
    1...5....10...15...20...25...30...35...40...45...50...55...60...65...70...75...80...85...90...95...1             
    4347565543675626556754563436456333665747645744435347574474453564336535364547755557745463676464464757             
    82433507C9C536B539F16A5D0779A01591F54A60A3A2365579A80195282328CA3260230CD852589732123363C8662FD85124             
                                                                                                                     
                                                                                                                     
     --- Record Number ---  3   ---  Record Length ---- 100                                                          
                                                                                                                     
    LGmdkr9jLIoaDI+582BxpnLB8ISfYc48F0s+B3Y9Gt0w4WwCm7LUalBUI4QUr5giKAlkykN64QbNWKPZpwvLWAOkyLphnKMyJQ9b             
    1...5....10...15...20...25...30...35...40...45...50...55...60...65...70...75...80...85...90...95...1             
    4466673644664423334776443456563343724353473735746345664543557366446676433564545577745446747664474536             
    C7D4B29AC9F149B582280EC289369348603B239974074773D7C51C2594152579B1CB9BE6412E7B0A076C71FB9C08EBD9A192             
                                                                                                                     
                                                                                                                     
     --- Record Number ---  4   ---  Record Length ---- 100                                                          
                                                                                                                     
    iTZFSbn3WgmecA9sbeWef+aqSgmQTqwMInn0AbjsxIzOd/pXrS7rD/Ph3PLMGboxN1zZISFi2miI547QiQ6yr3kA+ZYClsjZU/zU             
    1...5....10...15...20...25...30...35...40...45...50...55...60...65...70...75...80...85...90...95...1             
    6554566356666437665662675665577446634667747462757537425635444667437545463664333565377364255467655275             
    94A632E377D5319325756B1137D1417D9EE012A389AF4F0823724F0830CD72F8E1AA93692D995471916923B1BA93C3AA5FA5             
                                                                                                                     
                                                                                                                     
     --- Record Number ---  5   ---  Record Length ---- 100                                                          
                                                                                                                     
    HhImYcHB9nl6YXQyva64fBqcjwzFT7aEBkkJMvMoCSGpAWewCyBcgL8n+L6JeUv/ZvsIFV/pRJ7aeNvWEEDH/xkh2a2JtfK9Nse3             
    1...5....10...15...20...25...30...35...40...45...50...55...60...65...70...75...80...85...90...95...1             
    4646564436635557763364766774536446644746454745674746643624346572577445275436647544442766363476434763             
    889D93829EC6981961646213A7A647152BBAD6DF3370175739237C8EBC6A556FA63966F02A715E675548F8B8212A46B9E353             
                                                                                                                     
                                                                                                                     
     --- Record Number ---  6   ---  Record Length ---- 100                                                          
                                                                                                                     
    0wODqfZgZdqm02TtzBHQ2/lBsP1/BFv4w9jCQw8HPWDBuv6Kb19QSwMEFAAACAgAl2NDTm7R90f9BAAAxxoAABgAAAB4bC93b3Jr             
    1...5....10...15...20...25...30...35...40...45...50...55...60...65...70...75...80...85...90...95...1             
    3744765656763357744532647532447373645734554477346335574444444464634456353363444477644464444364336347             
    07F416A7A41D0244A2812FC2301F266479A317880742566B219137D561113171C2E44D729069211188F112711124239323A2             
                                                                                                                     
    *                         _                                                                                      
      ___ _ __   ___ ___   __| | ___                                                                                 
     / _ \ '_ \ / __/ _ \ / _` |/ _ \                                                                                
    |  __/ | | | (_| (_) | (_| |  __/                                                                                
     \___|_| |_|\___\___/ \__,_|\___|                                                                                
                _       _   _                                                                                        
      ___  ___ | |_   _| |_(_) ___  _ __                                                                             
     / __|/ _ \| | | | | __| |/ _ \| '_ \                                                                            
     \__ \ (_) | | |_| | |_| | (_) | | | |                                                                           
     |___/\___/|_|\__,_|\__|_|\___/|_| |_|                                                                           
    ;                                                                                                                
                                                                                                                     
    %utl_encodeBase64(inp=d:/xls/class.xlsx,out=d:/txt/class_encode.txt);                                            
                                                                                                                     
                                                                                                                     
                                                                                                                     
                                                                                                                     
                                                                                                                     
                                                                                                                     
                                                                                                                     
    *    _                    _                                                                                      
      __| | ___  ___ ___   __| | ___                                                                                 
     / _` |/ _ \/ __/ _ \ / _` |/ _ \                                                                                
    | (_| |  __/ (_| (_) | (_| |  __/                                                                                
     \__,_|\___|\___\___/ \__,_|\___|                                                                                
     _                   _                                                                                           
    (_)_ __  _ __  _   _| |_                                                                                         
    | | '_ \| '_ \| | | | __|                                                                                        
    | | | | | |_) | |_| | |_                                                                                         
    |_|_| |_| .__/ \__,_|\__|                                                                                        
            |_|                                                                                                      
    ;                                                                                                                
                                                                                                                     
                                                                                                                     
    ASCII Flatfile Ruler & Hex                                                                                       
    utlrulr                                                                                                          
    d:/txt/class_encode.txt                                                                                          
    d:/txt/class_encodeBase64.txt                                                                                    
                                                                                                                     
                                                                                                                     
     --- Record Number ---  1   ---  Record Length ---- 100                                                          
                                                                                                                     
    UEsDBBQAAAgIAJdjQ05BFyI5bAEAAKIFAAATAAAAW0NvbnRlbnRfVHlwZXNdLnhtbK2Uy07DMBBF90j8g+UtStyyQAgldMFjCZUo             
    1...5....10...15...20...25...30...35...40...45...50...55...60...65...70...75...80...85...90...95...1             
    5474445444644466533447436444444444454444534766566656546755464667643573344444336362575777546664464556             
    5534221111791A4A1052699521511B961114111170E62E2C2E2668C7A8E4CE842B259074D22690A87B543499117C4D6A3A5F             
                                                                                                                     
                                                                                                                     
     --- Record Number ---  2   ---  Record Length ---- 100                                                          
                                                                                                                     
    H2DsSePWL9luSf+eSYoqVJUm0G7iJPa591oeTzFpjCZrCFE5W9JxPqIErHBS2XlJ32fP2S0lMXEruXYWSrqBSCf3lxfFbOMhEqRt             
    1...5....10...15...20...25...30...35...40...45...50...55...60...65...70...75...80...85...90...95...1             
    4347565543675626556754563436456333665747645744435347574474453564336535364547755557745463676464464757             
    82433507C9C536B539F16A5D0779A01591F54A60A3A2365579A80195282328CA3260230CD852589732123363C8662FD85124             
                                                                                                                     
                                                                                                                     
     --- Record Number ---  3   ---  Record Length ---- 100                                                          
                                                                                                                     
    LGmdkr9jLIoaDI+582BxpnLB8ISfYc48F0s+B3Y9Gt0w4WwCm7LUalBUI4QUr5giKAlkykN64QbNWKPZpwvLWAOkyLphnKMyJQ9b             
    1...5....10...15...20...25...30...35...40...45...50...55...60...65...70...75...80...85...90...95...1             
    4466673644664423334776443456563343724353473735746345664543557366446676433564545577745446747664474536             
    C7D4B29AC9F149B582280EC289369348603B239974074773D7C51C2594152579B1CB9BE6412E7B0A076C71FB9C08EBD9A192             
                                                                                                                     
                                                                                                                     
     --- Record Number ---  4   ---  Record Length ---- 100                                                          
                                                                                                                     
    iTZFSbn3WgmecA9sbeWef+aqSgmQTqwMInn0AbjsxIzOd/pXrS7rD/Ph3PLMGboxN1zZISFi2miI547QiQ6yr3kA+ZYClsjZU/zU             
    1...5....10...15...20...25...30...35...40...45...50...55...60...65...70...75...80...85...90...95...1             
    6554566356666437665662675665577446634667747462757537425635444667437545463664333565377364255467655275             
    94A632E377D5319325756B1137D1417D9EE012A389AF4F0823724F0830CD72F8E1AA93692D995471916923B1BA93C3AA5FA5             
                                                                                                                     
                                                                                                                     
     --- Record Number ---  5   ---  Record Length ---- 100                                                          
                                                                                                                     
    HhImYcHB9nl6YXQyva64fBqcjwzFT7aEBkkJMvMoCSGpAWewCyBcgL8n+L6JeUv/ZvsIFV/pRJ7aeNvWEEDH/xkh2a2JtfK9Nse3             
    1...5....10...15...20...25...30...35...40...45...50...55...60...65...70...75...80...85...90...95...1             
    4646564436635557763364766774536446644746454745674746643624346572577445275436647544442766363476434763             
    889D93829EC6981961646213A7A647152BBAD6DF3370175739237C8EBC6A556FA63966F02A715E675548F8B8212A46B9E353             
                                                                                                                     
                                                                                                                     
     --- Record Number ---  6   ---  Record Length ---- 100                                                          
                                                                                                                     
    0wODqfZgZdqm02TtzBHQ2/lBsP1/BFv4w9jCQw8HPWDBuv6Kb19QSwMEFAAACAgAl2NDTm7R90f9BAAAxxoAABgAAAB4bC93b3Jr             
    1...5....10...15...20...25...30...35...40...45...50...55...60...65...70...75...80...85...90...95...1             
    3744765656763357744532647532447373645734554477346335574444444464634456353363444477644464444364336347             
    07F416A7A41D0244A2812FC2301F266479A317880742566B219137D561113171C2E44D729069211188F112711124239323A2             
                                                                                                                     
    *    _                    _                                                                                      
      __| | ___  ___ ___   __| | ___                                                                                 
     / _` |/ _ \/ __/ _ \ / _` |/ _ \                                                                                
    | (_| |  __/ (_| (_) | (_| |  __/                                                                                
     \__,_|\___|\___\___/ \__,_|\___|                                                                                
                 _               _                                                                                   
      ___  _   _| |_ _ __  _   _| |_                                                                                 
     / _ \| | | | __| '_ \| | | | __|                                                                                
    | (_) | |_| | |_| |_) | |_| | |_                                                                                 
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                
                    |_|                                                                                              
    ;                                                                                                                
                                                                                                                     
    * THIS IS THE ORIGINAL RAW EXCEL WORKBOOK BINARY FILE;                                                           
                                                                                                                     
    ASCII Flatfile Ruler & Hex                                                                                       
    utlrulr                                                                                                          
    d:/txt/class_encode.txt                                                                                          
    d:/txt/d:/xls/class_decode.xlsx                                                                                  
                                                                                                                     
                                                                                                                     
     --- Record Number ---  1   ---  Record Length ---- 100                                                          
                                                                                                                     
    PK.........cCNA."9l...........[Content_Types].xml...N.0.E.H...-J..@.%t.c..(.`.I../.nI..I.*T.&.n.$...             
    1...5....10...15...20...25...30...35...40...45...50...55...60...65...70...75...80...85...90...95...1             
    5400100000964441236000A00010005466766755776752766A9C4C314F4F8E24DB4027C609216E4ED2D64F9482592D6E2FBF             
    0B34400880733E1729C10025003000B3FE45E4F49053DE8DCD4BE300578C35DAC2085413958F0C936F9E9FE9AA4560E24697             
                                                                                                                     
                                                                                                                     
     --- Record Number ---  2   ---  Record Length ---- 100                                                          
                                                                                                                     
    Z.O1i.&k.Q9[.q>...pR.yI.g..-%1q+.v.J..H'....l.!..m,i...c,......`q.r....a.<.K>.v=..0.l....jPT#...."(.             
    1...5....10...15...20...25...30...35...40...45...50...55...60...65...70...75...80...85...90...95...1             
    514368260535D73A0A75D74D6CD22372B714B842F91C6E21A62699B628108BF67A7CF896C31430731D3E609BD655281A9220             
    AEF19C6B819B21E24C02999F7F9D511B966AA1877775C3124DC9D2F3CAACF930162104F1EC7BE76DAD01C2B24A04344F8289             
                                                                                                                     
                                                                                                                     
     --- Record Number ---  3   ---  Record Length ---- 100                                                          
                                                                                                                     
    d.Cz...X.....X....a..2%.[.6EI..Z..p.lm.....J..N.."y.......w.W...........17\.!!b.h........y.......S..             
    1...5....10...15...20...25...30...35...40...45...50...55...60...65...70...75...80...85...90...95...1             
    6C47E0C5ADA0C50ACB69A32058344BF5097066E97EA4094A027F0BEC8C7F5A2E0FEDFC1B335D226D68E8D80BA70F909CD5FD             
    4A3A16D8397BB8348A1C325FB965997A9E0FCD5EF6AA90ECC29418C4CE7A7DEBF31C2C9A17C9112A887E09E2F909626893C4             
                                                                                                                     
                                                                                                                     
     --- Record Number ---  4   ---  Record Length ---- 100                                                          
                                                                                                                     
    ..&a...yzat2...|.....O...I.2.(.!..g.. \..'...yK.f..._.D..x...@...!......6.......`e...d......A....[..             
    1...5....10...15...20...25...30...35...40...45...50...55...60...65...70...75...80...85...90...95...1             
    1126CCF77673BAB71980C4B80403F202A06B0258B2FB874F6F015E49D7DD14CF12DA8BFB3CBD08AF66DAD6EC1DDF4BF705FC             
    E2611169A142DE8CACFC5F64699238919170B0C0F78E99BF6B85F94EA8B6007F919D952D6773339605A634DC10B910DF4B83             
                                                                                                                     
                                                                                                                     
     --- Record Number ---  5   ---  Record Length ---- 100                                                          
                                                                                                                     
    ..C..=`....o_PK.........cCNn..G............xl/worksheets/sheet1.xml..]s.8...wf...}..?bg.t..M;..v6...             
    1...5....10...15...20...25...30...35...40...45...50...55...60...65...70...75...80...85...90...95...1             
    DC40036CBF865540010000096446DF4F000C100100076276767666772766673276699579318E76F0C7C836697E143DE73EEB             
    823F7D01AEAFF0B34400880733EE177D4007A0080008CF7F2B385543F385541E8DCD9D3B846F76F33D37F27C4A8DB3E66DE5             
                                                                                                                     
                                                                                                                     
     --- Record Number ---  6   ---  Record Length ---- 100                                                          
                                                                                                                     
    .... F.I._.. ...s.+.8~....8#V......d.Ey.G....2../.........jE....d......7...z...>0.<.P...A..*.....Z_.             
    1...5....10...15...20...25...30...35...40...45...50...55...60...65...70...75...80...85...90...95...1             
    0BA024C495B920E87928379F10325171BFC6C47E41AEB3112FDFC1ECCF64C8EA6DF1AF837FB71FB33A3A5DDF4AE20EFC0558             
    C2D906893FF204B03AB38EF3E9836FF59704D59D771F1259F77EFF4327A5BC6247E3BDF7FE1A42EE06CD067E19AA8A40AAF8             
                                                                                                                     
    * This is the original excel workbook;                                                                           
                                                                                                                     
    *    _                    _                                                                                      
      __| | ___  ___ ___   __| | ___                                                                                 
     / _` |/ _ \/ __/ _ \ / _` |/ _ \                                                                                
    | (_| |  __/ (_| (_) | (_| |  __/                                                                                
     \__,_|\___|\___\___/ \__,_|\___|                                                                                
               _       _   _                                                                                         
     ___  ___ | |_   _| |_(_) ___  _ __                                                                              
    / __|/ _ \| | | | | __| |/ _ \| '_ \                                                                             
    \__ \ (_) | | |_| | |_| | (_) | | | |                                                                            
    |___/\___/|_|\__,_|\__|_|\___/|_| |_|                                                                            
                                                                                                                     
    ;                                                                                                                
                                                                                                                     
    %utl_decodeBase64(inp=d:/txt/class_encode.txt,out=d:/xls/class_decode.xlsx);                                     
                                                                                                                     
    *                                                                                                                
     _ __ ___   __ _  ___ _ __ ___  ___                                                                              
    | '_ ` _ \ / _` |/ __| '__/ _ \/ __|                                                                             
    | | | | | | (_| | (__| | | (_) \__ \                                                                             
    |_| |_| |_|\__,_|\___|_|  \___/|___/                                                                             
                                                                                                                     
    ;                                                                                                                
                                                                                                                     
    * change outup to your autocall folder;                                                                          
                                                                                                                     
    filename ft15f001 "c:/oto/utl_encodeBase64.sas";                                                                 
    parmcards4;                                                                                                      
    %macro utl_encodeBase64(inp=,out=);                                                                              
                                                                                                                     
       /* Chang Chung */                                                                                             
       %put %sysfunc(ifc(%sysevalf(%superq(inp)=,boolean),**** Please Provide the input file       ****,));          
       %put %sysfunc(ifc(%sysevalf(%superq(out)=,boolean),**** Please Provide an output file       ****,));          
                                                                                                                     
        %let res= %eval                                                                                              
        (                                                                                                            
            %sysfunc(ifc(%sysevalf(%superq(inp)=,boolean),1,0))                                                      
          + %sysfunc(ifc(%sysevalf(%superq(out)=,boolean),1,0))                                                      
        );                                                                                                           
                                                                                                                     
         %if &res = 0 %then %do;                                                                                     
                                                                                                                     
             %utl_submit_py64("                                                                                      
             import base64;                                                                                          
             data = open('&inp', 'rb').read();                                                                       
             encoded = base64.b64encode(data);                                                                       
             with open('&out', 'wb') as f:;                                                                          
             .    f.write(encoded);                                                                                  
             ");                                                                                                     
                                                                                                                     
         %end;                                                                                                       
                                                                                                                     
    %mend utl_encodeBase64;                                                                                          
    ;;;;                                                                                                             
    run;quit;                                                                                                        
                                                                                                                     
    filename ft15f001 "c:/oto/utl_decodeBase64.sas";                                                                 
    parmcards4;                                                                                                      
    %macro utl_decodeBase64(inp=,out=);                                                                              
                                                                                                                     
       /* Chang Chung */                                                                                             
       %put %sysfunc(ifc(%sysevalf(%superq(inp)=,boolean),**** Please Provide the input file       ****,));          
       %put %sysfunc(ifc(%sysevalf(%superq(out)=,boolean),**** Please Provide an output file       ****,));          
                                                                                                                     
        %let res= %eval                                                                                              
        (                                                                                                            
            %sysfunc(ifc(%sysevalf(%superq(inp)=,boolean),1,0))                                                      
          + %sysfunc(ifc(%sysevalf(%superq(out)=,boolean),1,0))                                                      
        );                                                                                                           
                                                                                                                     
         %if &res = 0 %then %do;                                                                                     
                                                                                                                     
             %utl_submit_py64("                                                                                      
             import base64;                                                                                          
             with open('&inp', 'rb') as g:;                                                                          
             .    b64encode_from_file=g.read();                                                                      
             decoded=base64.b64decode(b64encode_from_file);                                                          
             with open('&out', 'wb') as w:;                                                                          
             .    w.write(decoded);                                                                                  
             ");                                                                                                     
                                                                                                                     
         %end;                                                                                                       
                                                                                                                     
    %mend utl_decodeBase64;                                                                                          
    ;;;;                                                                                                             
    run;quit;                                                                                                        
                                                                                                                     
                                                                                                                     
