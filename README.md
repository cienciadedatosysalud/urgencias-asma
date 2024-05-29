![Logo of the project](https://cienciadedatosysalud.org/wp-content/uploads/logo-Data-Science-VPM.png)

<small><i>This project follows the structure built using the [Common Data Model Builder](https://github.com/cienciadedatosysalud/cdmb), a tool that allows you to create common data models to facilitate interoperability and reproducibility of the analyses.</i></small>


# Caracterización pacientes adultos con crisis de asma atendidos en los servicios de urgencia
## Análisis de la continuidad asistencial del asma severa del adulto en Aragón después de atención urgente

Notas metodológicas y técnicas del modelo común de datos del proyecto de "Caracterización de pacientes adultos con crisis de asma atendidos en los servicios de urgencias", para el estudio de la continuidad asistencial del Asma severa del adulto en Aragón. 

Esta publicación se corresponde con la especificación del Modelo Común de Datos de este proyecto para la implementación de estos análisis en Aragón. 

# Objetivos
## Objetivo principal
El objetivo principal de este estudio es caracterizar los pacientes adultos que acuden a los servicios de urgencias hospitalarios por crisis de asma y evaluar su continuidad asistencial después de la atención urgente. 

## Objetivos específicos
- Caracterizar el tipo de pacientes que acuden a urgencias hospitalarias por crisis de asma
  - Identificar pacientes no diagnosticados de asma que debutan con una exacerbación de la enfermedad
  - Identificar pacientes con asma grave
  - Identificar las principales comorbilidades asociadas con asma grave
- Caracterizar los tratamientos recibidos por estos pacientes antes y después de la atención urgente por asma
- Evaluar la continuidad asistencial después de la atención urgente de estos pacientes en otras instancias y/o dispositivos asistenciales

# Diseño de estudio
Estudio observacional, retrospectivo, de los pacientes que acudieron a urgencias hospitalarias en cualquiera de los hospitales SNS de Aragón durante el año 2022 para el tratamiento de una crisis de asma (o síndromes relacionados) a partir de la reutilización de datos sanitarios.

## Definición de la cohorte
Pacientes adultos (mayores de 18 años) residentes en Aragón y con tarjeta sanitaria con al menos un episodio de asistencia en urgencias hospitalarias (o con un ingreso hospitalario no programado) con diagnóstico principal de asma moderada/severa (J45.4, J45.5, J45.90) durante el periodo de estudio.

### Criterios de inclusión
Adultos (18 años o mayores), residentes en Aragón, que hayan acudido a urgencias hospitalarias (o hayan ingresado en hospital de forma no programada) con un diagnósticos principal de asma persistente moderada o grave.

### Criterios de exclusión
- Menores de 18 años,
- Ingresos hospitalarios programados por cualquier diagnóstico,
- Pacientes con diagnóstico secundario en listado cie-10 {_E84%, P27%, Q254%, Q31%, Q32%, Q33%, Q34%, Q39%, Q893%_}

### Periodo de estudio: 
Desde el 1 de enero de 2022 hasta el 31 de diciembre de 2022.

---

# Detalles técnicos del contenido del respositorio (EN)
# Outputs
Outputs structure and content is described below including the files and folders that are generated when creating a research project with the `cdmb` Python library. There are four main folders corresponding to:

- __docs/CDM/__
  - **cdmb_config.json**: Configuration file.
  - **cohort_definition_inclusion.csv**: csv file that defines the criteria (i.e., codes) for inclusion in a cohort.
  - **cohort_definition_exclusion.csv**: csv file that defines the criteria (i.e., codes) for exclusion in a cohort.
  - **common_datamodel.xlsx**: The definition of the common data model in Excel format.
  - **entities/**: Folder structure where, for each defined entity, the catalogs and the established validation rules are stored.
  - **ER.gv, ER.gv.png**: an Entity-Relationship Diagram of the entities included in the CDM.
  - **synthetic-data/**: Folder structure contaning an automatically generated set of 1000 synthetic records per entity included en the CDM.
  - **hashed_files_list.json**: List of the files generated or used after generating the project with their md5 hash. This file must be kept hidden 
and should be used to cross-check with the results obtained from the analysis from the original input files.
- __inputs/__
  - **data.duckdb**: Database that temporarily contains the data entered by the user (synthetic data by default)
- __outputs/__
  - (Default directory of all the outputs produced in the project execution)
- __src/__
  - __analysis-scripts/__
    - (directory where the analysis scripts developed by the user are stored)
    - **r_report_template.qmd**: Quarto document, with an example analysis, showing the interaction with the folder structure and files generated in the project.
    - **_quarto.yml**: File containing the Metadata to execute Quarto documents.
  - __check_load-scripts/__
    - **check_load.py**: Script in charge of the mapping between the files introduced by the user (./inputs) and map them to the defined entities (inputs/data.duckdb). 
    In the loading process, the following checks are performed: Name of the variables match; the format/type of the variables match those established in the configuration.
    - __inputs/__: Auxiliary folder for the script 'check_load.py'.
  - __dqa-scripts/__
    - **dqa.py**: Data Quality Assesment script by default.
  - **validation-scripts/**
    - **validator.py**: Script in charge of applying the validation rules to the data.
    - **valididator_report.qmd**: Quarto document that generates a report in html from the results obtained from 'validator.py'. 
    - **_quarto.yml**: File containing metadata to execute Quarto documents.
- **ro-crate-metadata.json**: Accessible and practical formal metadata description for use in a wider variety of situations, 
from an individual researcher working with a folder of data, to large data-intensive computational research environments. For more information, visit [RO-Crate](https://www.researchobject.org/ro-crate/).
- **man_container_deployment.md**: From Data Science for Health Services and Policy Research group we provide in the following
  GitHub repository, a solution, for the deployment of the generated project. This step is optional.
- **LICENSE.md**: Project license (CC BY 4.0 by default).


## Requirements/Dependencies 
__*Note that dependencies may vary depending on user modifications!*__

## R dependencies
Version of Rbase used: **4.1**

Version of [Quarto](https://quarto.org/) used: **1.1.149**

| library    | version | link                                                                                    |
|------------|---------|-----------------------------------------------------------------------------------------|
| DuckDB     | 0.8.1   | https://duckdb.org/                                                                     |
| jsonlite   | 1.8.7   | https://cran.r-project.org/web/packages/jsonlite/index.html                             |
| kableExtra | 1.3.4   | https://cran.r-project.org/web/packages/kableExtra/vignettes/awesome_table_in_html.html |
| Hmisc      | 4.7.1   | https://cran.r-project.org/package=Hmisc                                                |

## Python dependencies
Version of Python used: **3.8**

| library         | version | link                                                    |
|-----------------|---------|---------------------------------------------------------|
| pandas          | 1.3.4   | https://pandas.pydata.org/                              |
| DuckDB          | 0.8.1   | https://duckdb.org/                                     |
| ydata_profiling | 4.1.2   | https://ydata-profiling.ydata.ai/docs/master/index.html |


# Authoring

| Surname, name | Affiliation | ![orcid](https://orcid.org/sites/default/files/images/orcid_16x16.png) ORCID |
|---------------|-------------|------------------------------------------------------------------------------|
Carretero Gracia, José Ángel (Investigador Principal)|Servicio de Neumología, Hospital Universitario Royo Villanova de Zaragoza (HURV)|[0000-0002-5933-0675](https://orcid.org/0000-0002-5933-0675)
Vera Solsona, Elisabet|Servicio de Neumología, Hospital Universitario Miguel Servet de Zaragoza (HUMS)|
Marrón Tundidor, Rafael|Servicio de Urgencias, Hospital Universitario Miguel Servet de Zaragoza (HUMS)|
Pérez Camo, Ignacio|Servicio de Alergología, Hospital Universitario Royo Villanova de Zaragoza (HURV)|
Estupiñán-Romero, Francisco|Instituto Aragonés de Ciencias de la Salud (IACS)|[0000-0002-6285-8120](https://orcid.org/0000-0002-6285-8120)
Bernal-Delgado, Enrique|Instituto Aragonés de Ciencias de la Salud (IACS)|[0000-0002-0961-3298](https://orcid.org/0000-0002-0961-3298)


# Previous version(s): 
Version 0.0.1

# How to contribute
- Repository: https://github.com/cienciadedatosysalud/urgencias-asma/
- Issue tracker: https://github.com/cienciadedatosysalud/urgencias-asma/issues

# References
- Data Science for Health Services and Policy Research group: https://cienciadedatosysalud.org/en/
- Common Data Model Builder library :https://github.com/cienciadedatosysalud/cdmb
- Analytic Software Pipeline Interface for Reproducible Execution (ASPIRE): https://github.com/cienciadedatosysalud/ASPIRE
- Atlas VPM community in Zenodo: https://zenodo.org/communities/atlasvpm
- Research Object Crate (RO-Crate): https://www.researchobject.org/ro-crate/
- ORCID: https://orcid.org/

<a href="https://creativecommons.org/licenses/by/4.0/" target="_blank" ><img src="https://img.shields.io/badge/license-CC--BY%204.0-lightgrey" alt="License: CC-BY 4.0"></a>

