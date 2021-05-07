# JSS 2021 – Replication package

Replication package of the paper titled "Mining Guidelines for Architecting Robotics Software" published at the International Journal of Systems and Software.

This study has been designed, developed, and reported by the following investigators:

- [Ivano Malavolta](https://www.ivanomalavolta.com) (Vrije Universiteit Amsterdam)
- [Grace Lewis](https://resources.sei.cmu.edu/library/author.cfm?authorID=4347) (Software Engineering Institute, Carnegie Mellon University)
- [Bradley Schmerl](http://www.cs.cmu.edu/~schmerl/) (Institute for Software Research, Carnegie Mellon University)
- [Patricia Lago](https://www.cs.vu.nl/~patricia/Patricia_Lago/Home.html) (Vrije Universiteit Amsterdam)
- [David Garlan](https://www.cs.cmu.edu/~garlan/) (Institute for Software Research, Carnegie Mellon University)

For any information, interested researchers can contact us by sending an email to any of the investigators listed above.
The full dataset including raw data, mining scripts, and analysis scripts produced during the study are available below.

## How to cite the dataset
If the dataset is helping your research, consider to cite it is as follows, thanks!

```
@article{JSS_ROS_2021,
  title = {{Mining guidelines for architecting robotics software}},
  journal = {Journal of Systems and Software},
  volume = {178},
  pages = {110969},
  year = {2021},
  issn = {0164-1212},
  doi = {https://doi.org/10.1016/j.jss.2021.110969},
  url = {https://www.sciencedirect.com/science/article/pii/S0164121221000662},
  author = {Ivano Malavolta and Grace A. Lewis and Bradley Schmerl and Patricia Lago and David Garlan}
}
```

### Overview of the replication package
---

This replication package is structured as follows:

```
    /
    .
    |--- data_analysis/       		The data that has been extracted during the iterative content analysis and the thematic analysis phases, and the R script for plotting the extracted data (see below).
    |--- dataset/             		The full dataset of ROS-based systems mined from GitHub, including also the Python scripts for rebuilding/updating the dataset and the raw data produced in all intermediate steps.
    |--- online_questionnaire/   	List of contacted participants, script for contacting all participants via email, raw data of the responses, transcript of the on-line questionnaire.
    |--- ICSE_SEIP_2020.pdf             A copy of the preliminary paper published at ICSE 2020
```

Each of the folders listed above are described in details in the remaining of this readme.

### Data analysis
---
```
data_analysis
    .
    |--- RQ1_codes_and_selection_criteria.pdf   The code we used for classifying each repository for answering RQ1 and the inclusion/exclusion criteria for selecting relevant repositories for our dataset    
    |--- analysis.r                             The R script we used for generating the plots reported in the article
    |--- documentation_fragments.csv            Raw textual fragments extracted from the documentation of ROS-based systems, with full traceability information about which guideline it generates and the specific repository it is coming from
    |--- guidelines_definitions.csv             Raw data containing the guidelines defined during the analysis for answering RQ2 with additional data about how we solved conflicts, their computed usefulness, etc.
    |--- thematic_map.csv             Raw data containing the thematic map between the raw code identified either in the GitHub repositories or in participants' responses and the guidelines (i.e., the themes).
```
The data in the CSV files has been manually, collaboratively, and iteratively extracted by the authors of the paper. The steps for recreating the plots presented in the paper the list of contributors to contact for replicating this study are presented [here](./INSTALL.md). 

### Dataset
---
```
dataset
    	.
	|--- manual_selection_gitlab.pdf                    16 out of 46 GitLab projects were not hosted on gitlab.com, so we performed all the filtering steps manually in those cases. This is the data we manually extracted about the 16 Gitlab repositories resulting from this manual step
	|--- repos_dataset_all.csv                          Automatically filtered repositories (598)
	|--- repos_dataset_selected.csv                     Manually filtered repositories (335)
	|--- repos_dataset_selected_sadoc.csv               Repositories containing a description of the software architecture of the robotic system (115)
	|--- repos_filtering_intermediate_numbers.pdf       Raw numbers about each single filtering step applied for building the dataset of ROS-based repositories
	|--- repos_filtering_statistics.pdf                 Tables showing descriptive statistics about the various repositories selected before and after the manual selection, and after the check about the architecture documentation
	|--- repos_golden_set.pdf                           Contains the list of repositories we knew a priori were good candidates for our study and we used such a set for (i) double check if our repository filtering steps were too strict and (ii) for piloting the manual analysis of the contents of the repositories
	|--- repos_mining_data/                             
	│   |--- Archive.zip                                Archive containing all the raw data related to our filtering steps, including intermediate data coming from GHTorrent, raw data produced by rosmap, and the raw data obtained at each single filtering step
	|--- repos_mining_scripts/                              
	    |--- cloner.py                                  Clones GitHub repositories based on a list provided as CSV file
	    |--- detector.py                                Given locally-cloned repositories, it detects which ones contain at least one ROS launch file (either in Python or XML)
	    |--- explorer.py                                Given the results of rosmap and GHTorrent, it performs all  filtering steps shown in Figure 4 in the paper (until step 9, step 10 is manual)
	    |--- ghtorrent_queries.sql                      Contains all SQL queries targeting GHTorrent  
	    |--- merge_counter.py                           Counts and merges duplicate results between rosmap and GHTorrent
	    |--- metrics_manager.py                         Computes a set of metrics on all targeted repositories (e.g., number of PRs, number of commits, etc.)
	    |--- visit_website.scpt                         Auxiliary script for programmatically visiting a given URL using Google Chrome in MacOS
```

Interested researchers can fully rebuild/update the whole dataset by following the steps presented [here](./INSTALL.md).

### Online questionnaire
---
```
online_questionnaire
    .
    |--- online_questionnaire.pdf                       Full transcript of the on-line questionnaire for contributors of repositories with architectural documentation
    |--- online_questionnaire_no_sa_doc.pdf                       Full transcript of the on-line questionnaire for contributors of repositories without architectural documentation
	|--- online_questionnaire_invitation_email.txt      Text of the email for inviting roboticists to participate to the on-line survey
	|--- online_questionnaire_responses.csv             All the responses of the on-line questionnaire, including our classification and codes
	|--- online_questionnaire_responses_raw.csv         Raw data containing all the responses of the on-line questionnaire, as it has been exported from the Google Drive spreadsheet
	|--- online_questionnaire_scripts/                   
	    |--- Mail Sender/                               
	    │   |--- README.md                              
	    │   |--- emails.csv                             The list of email addresses to target
	    │   |--- mailSender.py                          For each email address to target, it sends an (hard-coded)invitation email via the SendGrid API
	    |--- cloned_repos/                              Empty folder which will contain the cloned repositories
	    |--- cloned_repos.csv                           The list of cloned repositories from which to extract the list of contributors
	    |--- repos_to_clone.csv                         The list of repositories to clone
	    |--- cloned_repos_no_sa_doc.csv                 The list of cloned repositories without SA documentation from which to extract the list of contributors
	    |--- repos_to_clone_no_sa_doc.csv               The list of repositories without SA documentation to clone
```

The steps for contacting the list of contributors of the targeted GitHub repositories are presented [here](./INSTALL.md). 

## License

This software is licensed under the MIT License.
