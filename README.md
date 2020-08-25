To reproduce:

1. `npm install`
2. `npm start`

You will see the following output, including a tsc error

```
> @ start /home/alex/GitProjects/experiments/webpack-schema-utils-ajv-typescript-error-demo                                                                                                                                                                                               
> tsc                                                                                                                                                                                                                                                                                     
                                                                                                                                                                                                                                                                                          
node_modules/schema-utils/declarations/validate.d.ts:43:8 - error TS1259: Module '"/home/alex/GitProjects/experiments/webpack-schema-utils-ajv-typescript-error-demo/node_modules/ajv/lib/ajv"' can only be default-imported using the 'esModuleInterop' flag                             
                                                                                                                                                                                                                                                                                          
43 import Ajv from 'ajv';                                                                                                                                                                                                                                                                 
          ~~~                                                                                                                                                                                                                                                                             
                                                                                                                                                                                                                                                                                          
  node_modules/ajv/lib/ajv.d.ts:396:1                                                                                                                                                                                                                                                     
    396 export = ajv;                                                                                                                                                                                                                                                                     
        ~~~~~~~~~~~~~                                                                                                                                                                                                                                                                     
    This module is declared with using 'export =', and can only be used with a default import when using the 'esModuleInterop' flag.                                                                                                                                                      
                                                                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                                                                          
Found 1 error.                                                                                                                                                                                                                                                                            
                                                                                                                                                                                                                                                                                          
npm ERR! code ELIFECYCLE                                                                                                                                                                                                                                                                  
npm ERR! errno 2                                                                                                                                                                                                                                                                          
npm ERR! @ start: `tsc`                                                                                                                                                                                                                                                                   
npm ERR! Exit status 2                                                                                                                                                                                                                                                                    
npm ERR!                                                                                                                                                                                                                                                                                  
npm ERR! Failed at the @ start script.                                                                                                                                                                                                                                                    
npm ERR! This is probably not a problem with npm. There is likely additional logging output above.                                                                                                                                                                                        
                                                                                                                                                                                                                                                                                          
npm ERR! A complete log of this run can be found in:                                                                                                                                                                                                                                      
npm ERR!     /home/alex/.npm/_logs/2020-08-25T08_10_43_693Z-debug.log      
```

3. To fix you can navigate to ./node_modules/schema-utils/declarations/validate.d.ts then change line 43 from

```typescript
import Ajv from 'ajv';
```

to

```typescript
import * as Ajv from 'ajv';
```

4. Run `npm start` again and now the compilation succeeds.