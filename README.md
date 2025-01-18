### 1. General information

1. **Title:** Hate Crimes Against LGBTQIA+ People in Russia Found in Court Rulings (2010-2023)
2. **Creators:**
   - **Name:** Sergey Katsuba, **Affiliation:** University College Dublin, **Contact:** sergey.katsuba@ucdconnect.ie, **ORCID:** [0000-0001-8979-4211](https://orcid.org/0000-0001-8979-4211)
3. **Contributors:**
   - **Name:** Dataout Foundation (Stichting Dataout), **Role:** Data Manager, **Contact:** contact@dataout.org
4. **Persistent Identifier:** [https://doi.org/10.5281/zenodo.14250816](https://doi.org/10.5281/zenodo.14250816)
5. **Published on:** Zenodo
6. **Publication Date:** 30.11.2024
7. **Associated File Formats:** CSV, ZIP, TXT
8. **License:** [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/legalcode)
9. **Contact:** greyrainbow@dataout.org
10. **This documentation was updated on:** 18.01.2025

### 2. Motivation

1. This dataset was created for research purposes to investigate hate crimes against LGBTQIA+ people in Russia using court rulings as the primary source. Using official Russian portal of court rulings and two commercial legal databases, we extracted court rulings for 14 years (2010–2023) and identified 1296 hate crimes. This dataset is used within the project Grey Rainbow ([https://greyrainbow.dataout.org](https://greyrainbow.dataout.org)), the purpose of which is to document the consequences of discriminatory anti-LGBTQIA+ laws and collect reliable open data in the absence of official statistics on hate crimes in Russia. The Grey Rainbow project is a collaboration between Sergey Katsuba (University College Dublin, Dublin, Ireland) and Dataout Foundation (Stichting Dataout, The Netherlands), hereafter Dataout.

2. This dataset was created by Sergey Katsuba (University College Dublin) with contributions from Dataout.

3. No funding to declare. Dataout did not receive any funding to carry out work on this dataset.

### 3. Composition

1. The dataset consists of two types of instances: (1) a CSV table and (2) a ZIP archive with txt files. Each row in the CSV table represents a court ruling, in which we identified one or more hate crimes. In the CSV table, there are only properties associated with a court ruling, such as their identifiers or regions. In the ZIP archive, each txt file represents a court ruling with full text (in Russian). TXT file names in the ZIP archive correspond to the "filename" column in the CSV table.

2. The CSV table contains 948 rows. The ZIP archive contains 903 TXT files organised in 14 folders (2010–2023).

3. This dataset includes all court rulings and associated hate crimes we could identify and is not meant to be representative.
We collected all possible court rulings that were available on court websites and published in other legal databases and that contained search keywords we queried. Our sample is limited, because not all court rulings are being published online. In court rulings' text, we idnetified hate crimes againsts LGBTQIA+ people relying on a guide by OSCE to categorise such crimes.[^1] If different guides or criteria are used, the number of hate crimes might differ from the number of hate crimes we found.

	In reality, the number of hate crimes is larger due to the facts that not all victims report such crimes and not all reported cases end up in a court. To overcome this limitation, we looked at the yearly dynamic of hate crimes in our research.

4. In the CSV table, each row has 13 columns describing a court ruling and a hate crime identified in its text. In the example below, the court ruling with the number "1-87/2023" by a court in Karachayevo-Cherkessia region (with the code 09) contains 1 hate crime with 1 victim. The hate crime was premeditaded ("yes" in "premeditated_en"). There is a txt file name of the court ruling containing full text, which can be found in the ZIP archive as well as accessed online using a link in the last column "case_text_url".

	| year | case_number | filename        | region_code | region_name_ru                  | region_name_en         | article | n_fatalities | n_victims | n_crimes | premeditated_en | premeditated_ru | case_text_url                                                      |
    | :--- | :---:       | :---:          | :---:       | :---:                           | :---:                  | :---:   | :---:        | :---:     | :---:    | :---:           | :---:           | :---:                                                              |
    | 2023 | 1-87/2023   | 1_87_2023.txt  | 09          | Карачаево-Черкесская Республика | Karachayevo-Cherkessia | 163     | 0            | 1         | 1        | yes             | да              | https://court-cases-texts.s3.eu-west-1.amazonaws.com/1_87_2023.txt |

	**Data dictionary:**
   - **year:** Year of court hearing; Important: this year does not always coincide with the year when a crime was committed; we could not establish reliably in all cases when crimes were committed, because courts often redact such info
   - **case_number:** Court ruling number (not unique)
   - **filename:** TXT file name (in ZIP) with full text of the the corresponding court ruling; (str)
   - **region_code:** Russian region code accorging to the Main Directorate for Traffic Safety of the Ministry of Internal Affairs of Russia (or GIBDD), this codes are used by the Russian court website and indicate a region where a court is located; besides Russian regions, there are also two occupied Ukrainian territories Crimea (code 91) and Sevastopol (code 92)
   - **region_name_ru:** Region name (Russian)
   - **region_name_en:** Region name (English)
   - **article:** Criminal Code article number; multiple articles are possible; the article numbers with periods (for example "111.4") represent particular chapters of articles
   - **n_fatalities:** Number of fatalities
   - **n_victims:** Number of victims
   - **n_crimes:** Number of crimes
   - **premeditated_en:** Whether a crime was premeditated ("yes," "no," "unknown")
   - **premeditated_ru:** Russian translation of "premeditated_en" ("да", "нет", "неизвестно")
   - **case_text_url:** Link to full-text court ruling (same as the TXT files in in ZIP)

5. Some information is missing from the dataset instances. In the CSV table, 44 cases do not have links to their full texts. Respectively, the same cases do not have corresponding txt files in the ZIP archive with full texts, so the column "filename" also contains empty values. Among these 44 cases, 2 cases do not have case numbers, because it was impossible to determine them. Case "1-189/2019" has a missing value in the "article" column.

6. The relations between the CSV table and the cases texts in the ZIP archive are made explicit through the "filename" column. The cases in the CSV table can be aggregated by the columns "year", "region", "article", and "premeditated".

7. There are some errors in the dataset. The column "article" contains a few errors, such as missing or incorrect article numbers. We plan to correct these instances in future updates. There might be errors in the columns "n_fatalities", "n_victims", "n_crimes", "premeditated" due to the fact that this information was collected manually from court rulings' texts.

8. Although, the data we collected is public in its nature (it is released by Russian courts publicly on official websites), this dataset contains information that might be considered confidential. Such confidential information is released by courts by mistake. To minimise the risks of releasing confidential information by publishing our dataset (namely, the full texts of court rulings), we redacted potentially confidential information in court rulings' texts applying automatic methods and manual inspection. About the redaction process, see paragraph 14.

9. This dataset contains information that might be perceived as offensive, insulting, threatening, disturbing, or might otherwise cause anxiety. Such information is contained in the full texts of court rulings in TXT files. The court rulings often contain descriptions of violence, offensive or insulting phrases, and other textual information that might be disturbing to a reader. We did not redact such information, because it illustrates the nature of hate crimes.

10. This dataset is related to people. In the CSV table, we indicated the number of people that were victms of hate crimes, including cases with fatalities. In the TXT files, there are textual descriptions of people.

11. Although we did not explicitly identify any subpopulations in this dataset, we collected court rulings mentioning keywords related to LGBTQIA+ people. Sexual orientation and gender identity was relevant to our research when determining motives of hatred against LGBTQIA+ individuals. However, we did not aim to establish whether the victims belonged to this subpopulation and did not indicate it in any way in the dataset.

12. It is possible to identify individuals directly or indirectly using this dataset, namely the full texts of court rulings. The information related to individuals, such as judges, prosecutors, defenders, accused, or court secretaries, is openly published by Russian courts. The information identifying victims must be hidden, however, some courts do not redact such information fully by mistake. To minimise the risk of releasing information that could be used to identify individuals, including victims of hate crimes, we redacted information that may be linked to personal data in court rulings' texts. About the redaction process, see paragraph 14.

13. This dataset, namely full texts of court rulings, contains sensitive information, such as racial or ethnic origins, sexual orientation and gender identity, religious beliefs, political opinions, location, health information, criminal history, and other. To minimise the risk of linking these sensitive characteristics to real identifiable individuals, we redacted some information in the texts of court rulings. About the redaction process, see paragraph 14.

14. Despite the fact that Russian court rulings are public infomation availble to anyone online, their texts may contain personal and sensitive information that was not redacted by courts. We redacted the full texts of court rulings to minimise the risk of releasing potentially sensitive and personal information when publishing our dataset.

In each court ruling, we identified text spans with potentially sensitive/personal info, such as full names, full physical addresses, phone numbers, IP addresses, passport numbers, and emails. To identify full names, we reused a pre-trained language model for Russian from Spacy called "ru_core_news_lg".[^2] To identify other types of sensitive/personal info, we used regular expressions. We redacted the identified texts spans in all court rulings by replacing them with an ellipsis '[...]'. We reviewed the redacted court rulings manually checking whether there was no other potentially sensitive/personal information in them. However, we cannot guarantee that we redacted all potentially sensitive/personal information. For more detais on the redaction process and the code we used, please see [this Jupyter notebook](https://github.com/dataout-org/hate_crimes_2010_2023/blob/main/redacting_court_rulings.ipynb) in our GitHub repository.

### 4. Data collection process

1. The texts of court rulings were directly acquired from the following sources: the official portal of Russian court system "Pravosudie"[^3] that aggregates court rulings from all Russian courts; paid legal databases "Garant"[^4] and "Consultant Plus"[^5]. We used the paid databases when the free official portal was unavalable. In most cases, court rulings published by these databases are also freely available on the official court webites.

2. On the websites of the three sources mentioned in the paragraph above, we used search filters to retrieve court rulings: type of cases (criminal), year (2010 to 2023), and the level of court (first instance). In addition to the search filters, we used a set of keywords to find relevant court rulings. We reused the following keywords from related work:[^6] "нетрадиционный" ("non-traditional"), "гомосексуализм"" ("homosexuality"), "мужеложство" ("sodomy"), "лесбиянство" ("lesbianism"), "транссексуал" ("transsexual"), "меньшинство" ("minority"). These keywords represent discriminatory and offensive categories. We searched for them due to their frequent use in court rulings. To this set of keywords, we also added "ЛГБТ" ("LBGT").

3. The texts of court rulings obtained from the three aforementioned sources were manually reviewed to determine whether they described one or more hate crimes against LGBTQIA+ individuals. If a hate crime was identified, we extracted the details of both the court ruling and the hate crime to form a database (see Section 3 paragraph 4).

4. The data collection process was carried out by its creator, Sergey Katsuba.

5. The data was collected in 3 stages:
	1. Stage 1 (data for 2010-2020): September 2021 - April 2022
	2. Stage 2 (data for 2021-2022): February - April 2023
	3. Stage 3 (data for 2023): February - April 2024

8. No ethical review was conducted when collecting the data.

### 5. Preprocessing and cleaning

1. The initially obtained texts of court rulings had different file formats, such as DOC, DOCX, RTF, XML. We converted all the original files into the same format – TXT – to ease computational tasks of text processing and increase compatibility between text readers on different devices. We renamed the original files, so that their names correspond to the court case numbers.

2. We redacted potentially sensitive/personal information in the text of court rulings (see Section 3 paragraph 14). The redacted texts are contained in the ZIP archive. We do not publish the original non-redacted texts of court rulings due to the fact that they may contain sensitive/personal info that was not redacted by courts.

3. The software used to redact the texts of court rulings is available in our GitHub repository (see Section 3 paragraph 14).

4. The data that we extracted from the texts of court rulings is available separately in the CSV table (see Section 3).

### 6. Uses

1. This dataset has been used in research into the hate crimes against LGBTQIA+ people in Russia. Using the dataset, we determined in which Russian regions hate crimes were committed, the dynamics of these crimes over the 14 years period (2010–2023), whether the crimes were committed by organised groups or individuals, what the hate motives of attackers were, and whether judges recognised hate motives in these crimes. The results of this research have been published on the Grey Rainbow project website (https://greyrainbow.dataout.org) in English[^7] and Russian.[^8]

2. This dataset can be used for further investigation into the hate crimes against LGBTQIA+ people in Russia.

3. When reusing this dataset, it is important to consider its limitations (see Section 3 paragraph 3). This dataset should be used with caution given its sensitive content (see Section 3 paragraphs 8–13).

### 7. Maintenance

1. This dataset is published on Zenodo, supported and maintained by both its creator, Sergey Katsuba, and Dataout.

2. This dataset might be updated to correct errors or add new instances. The updates and their documenttation will be versioned on Zenodo. All versions of this dataset have [DOI](https://doi.org/10.5281/zenodo.14250816).

3. This documentation might be updated to correct errors or describe changes in the dataset. All versions of this documentation are available on [GitHub](https://github.com/dataout-org/hate_crimes_2010_2023/blob/main/README.md).

4. To extend, augment, build on, contribute to this dataset, one can upload a submission to the [Dataout Zenodo Community](https://zenodo.org/communities/dataout) or [open an issue on GitHub](https://github.com/dataout-org/hate_crimes_2010_2023/issues). For questions, comments, or suggestions, please send an email to greyrainbow@dataout.org.


**References**
[^1]: [Hate Crime Laws: A Practical Guide, 2nd Edition. Warsaw, 2022, OSCE/ODIHR](https://www.osce.org/odihr/523940)
[^2]: [Spacy, ru_core_news_lg](https://spacy.io/models/ru#ru_core_news_lg)
[^3]: [https://bsr.sudrf.ru](https://bsr.sudrf.ru)
[^4]: [https://www.garant.ru](https://www.garant.ru)
[^5]: [https://www.consultant.ru](https://www.consultant.ru)
[^6]: Kondakov, A. (2021). The influence of the ‘gay-propaganda’ law on violence against LGBTIQ people in Russia: Evidence from criminal court rulings. European Journal of Criminology, 18(6), 940-959. [https://doi.org/10.1177/1477370819887511](https://doi.org/10.1177/1477370819887511)
[^7]: On the grounds of hate: data from court rulings reveals the rise in crimes against LGBTQIA+ people in Russia, including premeditated group attacks, 13.01.2025, [https://greyrainbow.dataout.org/hate-crimes](https://greyrainbow.dataout.org/hate-crimes)
[^8]: На почве ненависти: данные из судебных решений показывают рост преступлений против ЛГБТК+ людей в России, в том числе организованных групповых нападений. Grey Rainbow, 30.11.2024, [https://greyrainbow.dataout.org/hate-crimes-ru](https://greyrainbow.dataout.org/hate-crimes-ru)

*When compiling this documentation, we reused "Datasheets for datasets": Timnit Gebru, Jamie Morgenstern, Briana Vecchione, Jennifer Wortman Vaughan, Hanna Wallach, Hal Daumé III, and Kate Crawford. 2021. Datasheets for datasets. Commun. ACM 64, 12 (December 2021), 86–92. [https://doi.org/10.1145/3458723](https://doi.org/10.1145/3458723)*
