# Placeholders/Variables

Placeholders can be translated in most cases. If you are uncertain, submit a query or contact LX. Variables, which are filled at run time or in the final output production, are never translated.

## Placeholders in Code Examples, URLs, or Paths

Translate placeholders if they are exposed for translation. 

source 	 https://<server name>:7001/CmcAppinstalldir/deployment
target	add your translation

*Add any language-specific instruction, or delete if not needed.*

## Placeholders in Date Formats 

Such placeholders appear in fields on the user interface and in text. Submit a query or contact LX to check whether you can translate these placeholders, or adjust the order to your locale (add reference to Dates).    

source 	This parameter is of type Date with the format MM/DD/YYYY. YYYY is the four-digit year, MM is the month (for example, January = 01), and DD is the number of days into the given month.
target	
add your translation 

*Add any language-specific instruction, or delete if not needed.*
  
## Variables 

Variables are not translatable, they are filled at run time, or in the final output production. 

source 	Description does not exist for unit &1 in language &2.
target	add your translation 
source 	This update is for #productname_short# #product_preversion#.
target	add your translation 

Even though authors are asked to avoid using variables that replace translatable text, you may come across it.  

*Add any language-specific instruction for handling variables, or delete if not needed. Examples may include:*
* use a colon and/or additional word 
* add a descriptor or additional word 

Description does not exist for &1. → Description does not exist for unit &1.

Description does not exist for &1. → Description does not exist for: &1 

Description does not exist for &1. → Description does not exist for the following: &1 

### Related Information 
* UI Elements 
* Cross-References, Hyperlinks, and Filepaths
