# Placeholders and Variables

Placeholders can be translated in most cases (submit a query or contact LX, if uncertain). Variables, which are filled at run time or in the final output production, are never translated.

<details><summary><b>Placeholders in Code Examples, URLs, or Paths</b></summary></br>

Translate placeholders if they are exposed for translation. </br>
  
| Source | Translation |
| --- | --- |
| https://`<server name>`:7001/CmcAppinstalldir/deployment | *add your translation* |</br>

*Add any language-specific instruction, or delete this sentence if not needed.*
</details>

## Placeholders in Code Examples, URLs, or Paths

Translate placeholders if they are exposed for translation. 
  
| Source | Translation |
| --- | --- |
| https://`<server name>`:7001/CmcAppinstalldir/deployment | *add your translation* |

*Add any language-specific instruction, or delete this sentence if not needed.*

## Placeholders in Date Formats 

Such placeholders appear in fields on the user interface and in text. Submit a query or contact LX to check whether they can be translated or the sequence of characters can be adjusted to the convention of the locale (see [Date, Time, Timezone, Calendar](template/04_locale-specific_conventions/date_time_timezone_calendar.md)).    

| Source | Translation |
| --- | --- |
| This parameter is of type Date with the format MM/DD/YYYY. YYYY is the four-digit year, MM is the month (for example, January = 01), and DD is the number of days into the given month. | *add your translation* |

*Add any language-specific instruction, or delete this sentence if not needed.*

  
## Variables 

Variables are not translatable, they are filled at run time, or in the final output production. 

| Source | Translation |
| --- | --- |
| Description does not exist for unit &1 in language &2. | *add your translation* |
| This update is for #productname_short# #product_preversion#. | *add your translation* |

Even though authors are asked to avoid using variables that replace translatable text, you may come across it.  

*Add any language-specific instruction for handling variables, or delete if not needed. Examples may include:*
* *use a colon and/or additional word* 
* *add a descriptor or additional word*

**Examples**
* Description does not exist for &1. → Description does not exist for unit &1.
* Description does not exist for &1. → Description does not exist for: &1 
* Description does not exist for &1. → Description does not exist for the following: &1 


### Related Information 
* UI Elements 
* Cross-References, Hyperlinks, and Filepaths
