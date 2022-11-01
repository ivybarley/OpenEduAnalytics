<img align="right" height="100" src="https://github.com/microsoft/OpenEduAnalytics/blob/main/docs/pics/oea-logo-nobg.png">

# Reading Progress Module
[Reading Progress](https://learn.microsoft.com/en-us/training/educator-center/product-guides/reading-progress/) is a free tool in Microsoft Teams that helps students practice their reading fluency through independent reading practice. With Reading Progress, students' reading performance can be reviewed and analyzed, and recommendations are provided on how students can improve their reading fluency.

Reading Progress data is available through Microsoft Educaation Insights and can be landed into your organization's data lake with our existing [OEA Microsoft Education Insights module](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights).

Education Insights requires the implementation of [Microsoft School Data Sync](https://sds.microsoft.com/) on O365, which provides school and class roster data, to enable its reports in Teams. For production data, you will need an O365 education tenant as Microsoft Education Insights is only enabled for education tenants.

 
## Problem Statement and Module Impact
Reading fluency is top of mind for many educators and parents. Defined as a reader’s ability to read text with accuracy, speed, and expression, reading fluency is a reliable factor to determining a student comprehends text.

Reading Progress, available in 100 languages, provides repeated oral reading practice for learners with the power of error analysis to identify how to support readers fluency. This relieves pressure for students, reduces classroom disruption, and redirects educator time to targeted instruction.

Reading Progress data can be used for different scenarios including:
- Dashboards for education leaders to track student fluency practice at a school or district level.
- Combining Reading Progress data with other data sources to show the relationship between reading fluency and other metrics like assessments and attendance, and student demographic data.

## Module Setup Instructions
1. Ensure you have proper [Azure subscription and credentials](https://github.com/microsoft/OpenEduAnalytics/tree/main/framework) and setup the [most recent version of OEA framework](https://github.com/microsoft/OpenEduAnalytics/tree/main/framework#setup-of-framework-assets). This will include the most recent version of the [OEA Python class](https://github.com/microsoft/OpenEduAnalytics/blob/main/framework/synapse/notebook/OEA_py.ipynb). 

2. Follow the setup instructions to deploy the [Microsoft Education Insights module](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights).


## Data Sources

This module imports digital activity and roster data for an education system via [School Data Sync](https://sds.microsoft.com/).
- [Digital Activity Data](https://docs.microsoft.com/en-us/schooldatasync/data-lake-schema-activity) provides a log of M365 signal activity from apps including Sharepoint, Teams Channel, Teams Meetings, Assignment Services, OneNote, Reading Progress, and Reflect.
- [Rostering Data](https://docs.microsoft.com/en-us/schooldatasync/data-lake-schema-rostering) is concerned with students, teachers, courses, and schools relationships.
- [Azure Active Directory Data](https://docs.microsoft.com/en-us/schooldatasync/data-lake-schema-azure-ad) provides people details and group memberships.

See the [module test data page](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights/test_data) for details on data format and contents.

## Module Components
Out-of-the box assets for this OEA module include: 
1. [Test Data](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights/test_data): Two artificially generated test data sets, which supports the module pipeline and Power BI template. Test data matches the [School Data Sync](https://sds.microsoft.com/) format exactly.
    - [K-12 Test Data](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights/test_data/k12_test_data): Test data formatted as a k-12 education system.
    - [Higher Education Test Data](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights/test_data/hed_test_data): Test data formatted as a higher education system.
2. [Pipeline Template](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights/pipeline): One main pipeline template which lands data into the Stage 1 data lake (for raw data) and processes into the Stage 2 data lake (for structured, queryable data). Stage 2 data is then made available via a serverless SQL endpoint.
3. [Notebooks](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights/notebook): 
    - [Insights_py.ipynb](https://github.com/microsoft/OpenEduAnalytics/blob/main/modules/module_catalog/Microsoft_Education_Insights/notebook/Insights_py.ipynb): A module python class notebook that defines the data schemas and basic functions of data ingestion and processing from Stage 1 to Stage 2.
    - [Insights_module_ingestion.ipynb](https://github.com/microsoft/OpenEduAnalytics/blob/main/modules/module_catalog/Microsoft_Education_Insights/notebook/Insights_module_ingestion.ipynb): Module data ingestion notebook which depends on the module class. The pipeline template incoporates this notebook. 
4. [PowerBI Template](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights/powerbi): A Power BI template which explores data in a basic way. The Power BI file is pre-loaded with test data making it easy to quickly interact with data. See instructions on the [module PowerBI page](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights/powerbi) to switch the dashboard data source to direct query from your Synapse workspace. Screenshots of the Power BI template are below.

## Additional Information
| Resource | Description |
| --- | --- |
| [Overview of Microsoft Education Insights](https://docs.microsoft.com/en-us/microsoftteams/class-insights) | Intro to Education Insights, what it can do, and what it can provide. |
| [School Data Sync (SDS) Overview](https://docs.microsoft.com/en-us/schooldatasync/) | Overview of SDS and reference to full documentation. |
| [Enable SDS Data Export](https://docs.microsoft.com/en-us/schooldatasync/enable-education-data-lake-export) | Instructions for landing SDS data in your data lake. |
| [Demo Tenant for Microsoft Education Insights](https://learn.microsoft.com/en-us/partner-center/mpn-demos) | Get access to a demo tenant provisioning that comes with demo data and demo scripts. |
| [Activity Data Information](https://docs.microsoft.com/en-us/schooldatasync/data-lake-schema-activity) | Reference to learn about the schema details for activity data ingested into stage 1. |
| [Azure Active Directory (AD) Data Information](https://docs.microsoft.com/en-us/schooldatasync/data-lake-schema-azure-ad) | Reference to learn about the schema details for AD data ingested into stage 1. |
| [Roster Data Information](https://docs.microsoft.com/en-us/schooldatasync/data-lake-schema-rostering) | Reference to learn about the schema details for roster data ingested into stage 1. |


## Contributions from the Community
 
The Microsoft Insights module [welcomes contributions](https://github.com/microsoft/OpenEduAnalytics/blob/main/docs/license/CONTRIBUTING.md).

This module was developed by [Kwantum Analytics](https://www.kwantumedu.com/). The architecture and reference implementation for all modules is built on [Azure Synapse Analytics](https://azure.microsoft.com/en-us/services/synapse-analytics/) - with [Azure Data Lake Storage](https://docs.microsoft.com/en-us/azure/storage/blobs/data-lake-storage-introduction) as the storage backbone,  and [Azure Active Directory](https://azure.microsoft.com/en-us/services/active-directory/) providing the role-based access control.

# Legal Notices
Microsoft and any contributors grant you a license to the Microsoft documentation and other content
in this repository under the [Creative Commons Attribution 4.0 International Public License](https://creativecommons.org/licenses/by/4.0/legalcode),
see the [LICENSE](LICENSE) file, and grant you a license to any code in the repository under the [MIT License](https://opensource.org/licenses/MIT), see the
[LICENSE-CODE](LICENSE-CODE) file.

Microsoft, Windows, Microsoft Azure and/or other Microsoft products and services referenced in the documentation
may be either trademarks or registered trademarks of Microsoft in the United States and/or other countries.
The licenses for this project do not grant you rights to use any Microsoft names, logos, or trademarks.
Microsoft's general trademark guidelines can be found at http://go.microsoft.com/fwlink/?LinkID=254653.

Privacy information can be found at https://privacy.microsoft.com/en-us/

Microsoft and any contributors reserve all other rights, whether under their respective copyrights, patents,
or trademarks, whether by implication, estoppel or otherwise.
