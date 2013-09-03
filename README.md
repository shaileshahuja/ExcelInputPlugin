<b>To add sTax streaming functionality to the existing Pentaho code, please follow these steps:</b>   
1. Merge given folder "excelinput" with "engine\src\org\pentaho\di\trans\steps\excelinput"  
2. Replace file "ui\src\org\pentaho\di\ui\trans\steps\excelinput\ExcelInputDialog.java" with given file "ExcelInputDialog.java"  
3. Build the code and run  
  
<b>To test the streaming functionality, perform the following steps:</b>  
1. Load the two transformations from the test folder  
2. Open the 'Microsoft excel input' step dialog.  
3. For the streaming stax poi test, spreadsheet type is "Excel 2007 XLSX (Apache POI Streaming)" and for normal poi test spreadsheet type is "Excel 2007 XLSX (Apache POI)" (Presetted)  
4. Browse and add the sample file given in the test folder (Data_400K.xlsx)  
5. Go to 'sheets' tab and click 'Get Sheets' (Notice the speed here)  
6. Go to 'fields' tab and click 'Get Fields' (Notice the speed here)  
7. Open the 'Text file output' step dialog.  
8. Enter the appropriate filename here such as "ExcelStaxPoiOutput" or "ExcelPoiOutput".  
9. Go to 'fields' tab and click 'Get Fields'  
10. Run the transformation (notice the speed here)  
  
If your Pentaho is running on a normal PC, you will probably be stuck Step (5) for the normal poi test. You may need to increase memory assigned to make this test work (otherwise just give up and use stax poi).
This test should clearly illustrate the huge performance difference between the two types of APIs.  
  
<b>Things to take note for stax poi:</b>  
1. Please follow the steps properly, not all functions are supported.  
2. If you investigate the code, there will be a lot of nested ifs and while loops. This is how it works for now, I will upload a better design later.  
3. The best part is that the current KWorkbook, KSheet and KCell interfaces were used, making no change to architecture of the plugin. Although this makes things tricky and I am not sure if it will work when all features will need to be implemented.  
4. All data is treated as type "String". Formula evaluation is not supported (and will never be). The checkboxes in the excel input plugin need to remain as is, otherwise the code will fail for now.  
  
  
Tested on Windows 7 64 bit
