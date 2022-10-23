# Learning Analytics Package: Microsoft Teams Meetings

The OEA Learning Analytics Package: Microsoft Teams Meetings contains a set of assets that provides a professor or school leader with insights on learners' digital activity in Microsoft Teams Meetings at a class or course level. 

Data from apps that provide Microsoft Teams Meeting activity including Microsoft Education Insights and Microsoft Graph can be combined with other data sources for different Learning Analytics use cases. 

This package was primarily developed for higher education but can be modified for K-12 scenarios.

1. <ins>Guidance and documentation:</ins> This package provides guidance on the end-to-end process of developing a Learning Analytics use case project for Microsoft Teams Meetings through the problem statement and package impact. The [OEA Use Case Documentation](https://github.com/microsoft/OpenEduAnalytics/blob/main/docs/use_cases/Open_Education_Analytics_Use_Case_Template_v3.docx) should be completed when developing the production-level implementation of this package, including: how to engage stakeholders in the project, prior research on the use case problem domain and theory, how to map data sources to the theory of the problem, and how to implement Microsoft’s Principles of Responsible Data and AI. <em> It is highly recommended this document be reviewed and completed by any education system considering using this package, and that the documentation be revised to the specific data and decisions for that system’s context. </em>

2. <ins>Technical assets:</ins> Various assets are freely available in this package to help accelerate implementation of Learning Analytics use cases. Assets include descriptions of data sources, notebooks for data processing, a pipeline for data model building and deployment, and sample Power BI dashboards. See descriptions of technical assets below.

## Problem Statement and Package Impact
With varied modes of learning, learning platforms and learner needs, educators have difficulty determining how students participate and learn in a class or course in-person, remote and in hybrid settings. Due to this, educators are not able to consolidate student learning activities and progress.

The Learning Analytics: Microsoft Teams Meetings package provides dashboards that bring together signals from Microsoft Teams Meetings of how students learn and complete a course to help educators improve overall class participation. Educators can identify which courses, classes and students have lower or higher engagement in Microsoft Teams Meetings and the trends over time.

The assets in this package can be combined with course completion, academic assessments, graduation rates, competency measures, mastery data, or other outcome data to identify how patterns of engagement relate to learning outcomes.

## Package Setup Instructions
![](https://github.com/ivybarley/OpenEduAnalytics/blob/main/packages/package_catalog/Learning_Analytics_Microsoft_Teams_Meetings/docs/images/Learning_Analytics_Microsoft_Teams_Package_Setup_Instructions.png)

<ins><strong>Preparation:</ins></strong> Ensure you have proper [Azure subscription and credentials](https://github.com/microsoft/OpenEduAnalytics/tree/main/framework) and setup [v0.6.1 of the OEA framework](https://github.com/microsoft/OpenEduAnalytics/tree/main/framework#setup-of-framework-assets). This will include v0.6.1 of the [OEA Python class](https://github.com/microsoft/OpenEduAnalytics/blob/main/framework/synapse/notebook/OEA_py.ipynb).

1. Examine available data sources. See [below](https://github.com/ivybarley/OpenEduAnalytics/tree/main/packages/package_catalog/Learning_Analytics_Microsoft_Teams_Meetings#data-sources) for these related data sources. Choose which modules or data sources to implement.
    * This package was developed using the following modules: [Contoso SIS](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Student_and_School_Data_Systems), [Microsoft Education Insights](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights), and [Microsoft Graph Reports API](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Graph). 
    * Run each of the module data pipelines to ingest the data into stage 2. 
2. Use the [Digital Engagement Schema pipeline](https://github.com/microsoft/OpenEduAnalytics/tree/main/schemas/schema_catalog/Digital_Engagement_Schema/pipeline) and process the compatible modules you choose to ingest. This will combine all module-tables into a unified table, and creates a single database for the Power BI dashboard. Visit the [Data](https://github.com/ivybarley/OpenEduAnalytics/tree/main/packages/package_catalog/Learning_Analytics_Microsoft_Teams_Meetings/data) page for a detailed explanation of its use in the Power BI data model.
3. Import and run the [Learning Analytics: Microsoft Teams Meetings pipeline template](https://github.com/ivybarley/OpenEduAnalytics/tree/main/packages/package_catalog/Learning_Analytics_Microsoft_Teams_Meetings/pipeline) to combine SIS data sources into a Power BI data model like the example provided in the [Data](https://github.com/ivybarley/OpenEduAnalytics/tree/main/packages/package_catalog/Learning_Analytics_Microsoft_Teams_Meetings/data) page.
    * This package pipeline aggregates SIS data from the [Microsoft Education Insights](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights) and [Contoso SIS](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Student_and_School_Data_Systems) modules into a single student table for details on the specific tables being used.
4. Use the Power BI dashboard to explore Learning Analytics: Microsoft Teams Meetings. Note that all pipelines create SQL views which can be accessed via your Synapse workspace Serverless SQL endpoint. Example dashboard concepts are [provided in this package](https://github.com/ivybarley/OpenEduAnalytics/tree/main/packages/package_catalog/Learning_Analytics_Microsoft_Teams_Meetings/powerbi).
      *  More detailed information on the queries used are provided in the [Power BI folder](https://github.com/ivybarley/OpenEduAnalytics/tree/main/packages/package_catalog/Learning_Analytics_Microsoft_Teams_Meetings/powerbi). 
      
## Data Sources
This package combines multiple data sources: 
* <strong>School Information System (SIS)</strong>: School, grade level, and class roster.
* <strong>Digital Engagement data (Microsoft Teams Meetings) </strong>: Application use, type of engagement (log-ins, meeting attendance duration, etc), date of the activity, and user information of the activities.

This package can use several [OEA Modules](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules) to help ingest data sources that are typically used to understand patterns seen in Learning Analytics (see below for list of relevant OEA modules). 

| OEA Module | Description |
| --- | --- |
| [Student and School Data Systems](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Student_and_School_Data_Systems) | Fictitious student in-person attendance data. |
| [Microsoft Education Insights](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights) | For Microsoft engagement/activity data, and can be used for SIS data. |
| [Microsoft Graph](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Graph) | For other forms of Microsoft engagement/activity data. |
| [Ed-Fi Data Standards](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/Education_Data_Standards/Ed-Fi) | For typical Student Information System (SIS) data, including school rosters, grade level and demographic information. N.B: The Ed-Fi module creation is still in progress. |

These modules are then combined into single tables based on the types of data contained with them, using the [OEA schemas](https://github.com/microsoft/OpenEduAnalytics/tree/main/schemas) to ingest and transform the module data so that only the relevant columns are extracted from the stage 2 data. Below is the list of relevant OEA schema definitions used in this package.

| OEA Schema | Description |
| --- | --- |
| [Digital Engagement Schema](https://github.com/microsoft/OpenEduAnalytics/tree/main/schemas/schema_catalog/Digital_Engagement_Schema) | For extracting forms digital engagement into a standardized OEA schema. |


## Package Components 
Sample out-of-the box assets for this OEA package include: 
1. [Data](https://github.com/ivybarley/OpenEduAnalytics/tree/main/packages/package_catalog/Learning_Analytics_Microsoft_Teams_Meeting/data): For understanding the data relationships and standardized schema mappings used for certain groups of data.
2. [Documentation](https://github.com/ivybarley/OpenEduAnalytics/tree/main/packages/package_catalog/Learning_Analytics_Microsoft_Teams_Meeting/docs): 
      * [OEA Use Case Documentation Template](https://github.com/microsoft/OpenEduAnalytics/blob/main/docs/use_cases/Open_Education_Analytics_Use_Case_Template_v3.docx). 
      * More detailed instructions for migrating from test data use to production data use.
3. [Notebook](https://github.com/ivybarley/OpenEduAnalytics/tree/main/packages/package_catalog/Learning_Analytics_Microsoft_Teams_Meeting/notebooks): For aggregating, enriching, and curating data within the data lake.
4. [Pipeline](https://github.com/ivybarley/OpenEduAnalytics/tree/main/packages/package_catalog/Learning_Analytics_Microsoft_Teams_Meeting/pipeline): For the overarching data processing (i.e., aggregation, subsetting, schema transformation, etc.), and support for Power BI dashboards.
5. [Power BI Template](https://github.com/ivybarley/OpenEduAnalytics/tree/main/packages/package_catalog/Learning_Analytics_Microsoft_Teams_Meeting/powerbi): For exploring, visualizing, and deriving insights from the data.

The Learning Analytics Package: Microsoft Teams Meetings [welcome contributions.](https://github.com/microsoft/OpenEduAnalytics/blob/main/docs/license/CONTRIBUTING.md) 

This package was developed by Microsoft Education. The architecture and reference implementation for all modules is built on [Azure Synapse Analytics](https://azure.microsoft.com/en-us/services/synapse-analytics/) - with [Azure Data Lake Storage](https://docs.microsoft.com/en-us/azure/storage/blobs/data-lake-storage-introduction) as the storage backbone,  and [Azure Active Directory](https://azure.microsoft.com/en-us/services/active-directory/) providing the role-based access control.

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
