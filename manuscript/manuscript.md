---
layout: article
title: Ten Simple Rules for Digital Data Storage
tags: []
bibliography: resources/manuscript.bib
csl: resources/plos.csl
author:
 - family: Hart
   given: Edmund
   affiliation: 1
   email: edmund.m.hart@gmail.com
 - family: Barmby
   given: Pauline
   affiliation: 2
 - family: Hollister
   given: Jeffrey
   affiliation: 3
 - family: LeBauer
   given: David
   affiliation: 4
 - family: Zimmerman
   given: Naupaka
   affiliation: 5
 - family: Woo
   given: Kara H.
   affiliation: 6
 - family: Mount
   given: Sarah
   affiliation: 7
 - family: Poisot
   given: Timothée
   affiliation: 8
 - family: Michonneau
   given: François
   affiliation: 9

organization:
 - id: 1
   name: Univeristy of Vermont
   address: Department of Biology, Burlington
 - id: 2
   name: University of Western Ontario
   address: Department of Physics and Astronomy
 - id: 3
   name: US Environmental Protection Agency
   address: Atlantic Ecology Division
 - id: 4
   name: University of Illinois at Urbana-Champaign
   address: National Center for Supercomputing Applications and Institute for Genomic Biology
 - id: 5
   name: University of Arizona
   address: School of Plant Sciences
 - id: 6
   name: Washington State University
   address: Center for Environmental Research, Education, and Outreach
 - id: 7
   name: University of Wolverhampton
   address: School of Mathematics and Computer Science
 - id: 8
   name: Université de Montréal
   address: Département de Sciences Biologiques
 - id: 9
   name: University of Florida
   address: iDigBio, Florida Museum of Natural History, Gainesville, FL 32611-7800
---

\linenumbers

# Introduction {-}

<!-- JWH Comments: May want to add a few more examples on top of DNA
sequencing and sensor networks.  I am thinking LHC and astronomy, but
outside my field so don't know good one.  Some references for those
too could also be added. I removed the second mention of
heterogeneity, seemed redundant. -->

Data is the central currency of science, but the nature of scientific data has
changed dramatically with the rapid pace of technology. This change led to an
increasing heterogeneity of data formats, dataset sizes, data complexity, and
data use cases (up to the importance of data sharing). For example, improvements
in high throughput DNA sequencing, sustained institutional support for large
sensor networks [@Reid2014, @Hampton2013], and sky surveys with large-format
digital cameras [@Eisenstein2011] created massive quantities of data. At the
same time, increasingly common collaboration between researchers [@Adams2012]
necessitates increased coordination data collectors [@Fraser2013]. As a
consequence, "data" can now mean anything from petabytes of information stored
in professionally-maintained databases, through spreadsheets on a single
computer, to hand-written tables in lab notebooks on shelves. All remain
important, but methods of data curation must continue be updated in order to
encompass the changes brought about by new forms and practices of data
collection and storage.

While much has been written about both the virtues of data sharing
[@Wolkovich2012, @Roche2014] and best practices to do so [@White2013,
@Goodman2014], how to store data has received comparatively less attention.
Proper storage is a prerequisite to sharing, and indeed inadequate storage lack
contributes to the phenomenon of data decay or "data entropy": data, whether
publicy shared or not, becomes less accessible through time [@Pepe2014,
@Vines2014, @Michener2012, @Michener1997]. Best practices for data storage often
begin and end with "use a community standard repository" and this is, by all
means, a great practice. However, data storage policies are highly variable
between repositories [@Marcial2010], and best practices across all stages of the
data life cycle will facilitate transition from local storage to repository.
Good storage practices are important even (or especially) in cases where data
may not fit with an existing repository, or in the cases where only derived data
products (versus raw data) are suitable for deposition, or in the case where an
existing repository may have lax standards. Therefore, this manuscript describes
10 simple rules for digital data storage that grew out of a long discussion
among instructors for the Software Carpentry initiative [@Wilson2014]. Software
Carpentry instructors are scientists from diverse backgrounds who have
encountered a variety of data storage challenges and are active in teaching
other scientists best practices for scientific computing and data management.
Thus, this paper represents a distillation of collective experience, and
hopefully will be useful to scientists facing a variety of data storage
challenges.


<!--   Original intro thoughts
Much advice has been written on both the nature of sharing data

- Data is the lifeblood of science.
- Yet the how, when and where of storing the data is not often given much thought.
- This can have some unforeseen and sometimes unfortunate consequences
    - examples of where poor data management/storage caused big problems?
- Best practices for storing data are different than best practices
  for sharing/publishing data.
    - Often publishing data best practices are more standard, (e.g. [@White2013])
    - Best practices can sometimes be discipline specific

- Avoiding these potential problems is possible if scientist and their
  research collaborators practice some simple rules.

- A discussion about this topic took place on the SWC mailing list
- In this mansucript we have distilled the essence of that discussion
  into 10 simple rules, if followed, will help facilitate quick,
  robust analysis, allow others to re-use your data for new insights,
  and serve as a record of the work that lives beyond a single
  publication.  -->

# Rule 1: Know what to expect {-}

One can avoid most of the troubles encountered during the analysis, management,
and release of data by having a clear roadmap of what to expect *before* data
acquisition starts. For instance:

 - How will the raw data be received? Are they delivered by a machine or software, or typed-in?
 - What is the format expected by the software used for analysis?
 - Is there a community standard on the format for release?

The answers to these questions can range from simple cases (e.g., sequencing
data stored in the FASTA format, which can be used as is throughout the
analysis), to experimental designs involving multiple instruments, each with its
own output format and conventions. Knowing the state in which the data needs to
be at each step can help (i) identify software tools to use in converting across
data formats, (ii) orient technological choices about how and where the data
should be stored, and (iii) rationalize the analysis pipeline, making it more
amenable to re-use.

Also key is the ability to estimate the storage volume needed to store the data,
both during and after the analysis. The required strategy will differ for
datasets of varying size. 'Lighter' datasets (e.g. datasets that are only a few
megabytes in size) can be managed locally with a simple data management plan,
whereas larger datasets (e.g. gigabytes to terabytes and even petabytes) will in
almost all cases require careful planning and preparation (Rule 9).

# Rule 2: Know your use case {-}

Well identified use cases make data storage easier. Ideally prior to beginning
data collection, one can answer the following questions:

 - Should the raw data be archived (Rule 3)?
 - Should the data used for analysis be prepared once, or re-generated
   from the raw data each time (and what difference would this choice
   make for storage, computing requirements, and reproducibility)?
 - Will manual corrections be necessary (as opposed to programmatic
   approaches)?
 - How will changes to the data be tracked, and where will these
   tracked changes be logged?
 - Will the final data be released, and if so, in what format?
 - Are there restrictions or privacy concerns associated with the data
   (e.g. for survey results, threatened species)?
 - Will institutional validation be required prior to releasing the
   data?
 - Does the funding agency the research mandates data deposition, and
   if so, where?
 - Does the target journal mandates data deposition?

None of these questions have universal answers, nor are they the only questions
one should ask before starting data acquisition. But as for Rule 1, knowing the
what, when, and how of *your* use of the data will bring you close to a reliable
roadmap on how to handle data from acquisition through publication to archival.

# Rule 3: Keep raw data raw {-}

Since analytical and data processing procedures improve or otherwise change over
time, having access to the 'raw' (unprocessed) data can facilitate future
re-analysis and analytical reproducibility. As processing algorithms improve and
computational power increase, new analyses will be enabled that were not
possible at the time of the original work. If only derived data are stored, it
can be difficult to impossible for other researchers to confirm analytical
results, to assess the validity of statistical models, or to directly compare
findings across studies.

Therefore, data should always be kept in raw format whenever possible (within
the constraints of technical limitations). In addition to being the most
appropriate way to ensure transparency in analysis, having the data stored and
archived in their original state gives a common point of reference for
derivative analyses. What constitutes sufficiently "raw" data is not always
clear (e.g., ohms off a temperature sensor or images off an Illumina sequencing
flowcell are generally not archived after the initial processing). Yet the
spirit of this rule is that data should be as "pure" as possible when they are
stored. If derivations occur, they should be documented by also archiving
relevant code and intermediate data sets.

The US National Ecological Observatory Network (NEON) handles this issue with a
schema for various "levels" of data products that pertain to the amount of
processing performed on each ([see here for a brief overview][neon]). In this
case, raw data can include such products as voltage measurements or unprocessed
LIDAR returns. These represent a tremendous amount of data; sharing them often
requires physically sending a hard drive through the postal service. NEON has
handled this by writing detailed "Algorithm Theoretical Basis Documents"
(ATBD's) documenting the different processing "levels". This approach follows
one developed for the NASA EOSDIS program, and explicits the step between raw
and user-facing data. These levels, which start at 0 for raw data, and increase
with the amount of derivation and processing, are also analogous to the levels
used by the National Aeronautics and Space Administration (NASA) and National
Oceanic and Atomospheric Administration (NOAA) [uses for satellite data
sets][noaa].

[neon]: http://www.neoninc.org/science-design/data-processing
[noaa]: http://www.ngdc.noaa.gov/wiki/index.php?title=NOAA_Processing_Levels

<!-- NZ comment: do we need to be aware of being US-centric here? -->
<!-- Perhaps readers elsewhere will not recognize all of these US -->
<!-- federal agencies or would appreciate references from other -->
<!-- countries? -->

# Rule 4: Store data in open formats {-}

To maximize accessibility and long-term value, it is preferable to store data in
formats whose specifications are freely available. The appropriate file type
will depend on the data being stored (e.g. numeric measurements, text, images,
video), but the key idea is that accessing data should not require proprietary
software, hardware, or a license. Proprietary formats change, maintaining
organizations go out of business, and changes in license fees make access to
data in proprietary formats unaffordable to end-users. Examples of open data
formats include comma-separated values (CSV) for tabular data, hierarchical data
format (HDF) and NetCDF for hierarchically structured scientific data, portable
network graphics (PNG) for images, and extensible markup language (XML) for
documents. Examples of closed formats include DWG (for AutoCAD drawings),
Photoshop document (PSD, for bitmap images), Windows Media Audio (WMA), and
Microsoft Excel. Even if day-to-day processing uses closed formats, for example
due to software requirements, data being stored for archival purposes should be
so in open formats. This is generally not prohibitive; most closed-sourced
software enables users to export data to an open format.

# Rule 5: Data should be uniquely identifiable {-}

To aid reproducibility, the data used in a scientific publication should be
uniquely identifiable.  Ideally, datasets should have a unique identifier such
as a Document Object Identifier (DOI), Archival Resource Key (ARK), or a
Persistant URL (PURL).  An increasing number of online services, such as
[Figshare](http://figshare.com/), [Zenodo](http://zenodo.org), or
[DataOne](http://www.dataone.org) are able to provide these. Institutional
initiatives also exist, and are known to your librarians.

Datasets evolve over time. In order to distinguish between different versions of
the same data, each dataset should have a distinct name, which includes a
version identifier. A simple way to do this is to use date stamps as part of the
dataset name. Using the ISO 8601 standard avoids regional ambiguities: it
mandates the date format `YYYY-MM-DD` (i.e. from largest time unit to smallest).
For example, the date "February 1st, 2015", while written as `01-02-2015` in the
UK and `02-01-2015` in the US, is the unambiguous `2015-02-01` under this
standard.

*Semantic versioning*, as described in [@semver2014], is a richer approach to
solving the same problem. The CellPack datasets are an example of this
[@johnson2014cellpack]. A semantic version number takes the form:
`Major.Minor.Patch`, e.g. `0.2.7`. The *major version* numbers should be
incremented (or *bumped*) when a dataset scheme has been updated, or some other
change is made that is not compatible with previous versions of the data with
the same major version number. This means that an experiment using version
`1.0.0` of the dataset may not run on version `2.0.0` without  changes to the
data analysis. The *minor version* should be bumped when a change has been made
which is compatible with older versions of the data with the same Major version.
This means that any analysis that can be performed on version `1.0.0` of the
data is repeatable with version `1.1.0` of the data. For example, adding a new
year in a temporal survey will result in a bump in the minor version. The *patch
version* number is bumped when typos or bugs have been fixed. For example
version `1.0.1` of a dataset may fix a typo in version `1.0.0`.

# Rule 6: Link relevant metadata {-}

It should be almost impossible to separate data from its associated metadata.
The importance of metadata for context, reusability, and discovery has been
written about at length in many guides for data best practices [@Michener2012,
@Strasser2012 , @White2013].

Metadata should be as comprehensive as possible, use the relevant standards of
your discipline, and be machine-readable (e.g., XML, JSON). Metadata should
always accompany a data set, wherever it is stored. How best to do this depends
on the format of the data. Formats such as NetCDF or HDF5 allow for embedded
metadata, so the data and metadata are bundled together. In a relational
database, metadata tables should be clearly labeled and linked to the relevant
data. Ideally a schema will be provided that also shows the linkages between
data tables and metadata tables. Another scenario is a set of flat text
files--in this case a semantically versionned, compressed archive should be
created that includes metadata file(s).

Whatever format is used for archiving, the goal should be to make the link
between metadata and data as clear as possible. The best approach is dependent
on the archiving plan used, but even if the data set is archived solely for
personal use, metadata will provide crucial context for future reuse.

<!-- PB comment: do we need references for NetCDF or HDF5? -->
<!-- NZ comment: I think so. Not everyone may be familiar with them -->

# Rule 7: Adopt the proper privacy protocols {-}

In data sets where privacy is important, be sure to have a plan in place to
protect data confidentiality. You should consider the different data
stakeholders when developing privacy protocols for your data storage. These
stakeholders include funding agencies, human subjects or entities,
collaborators, and yourself. Both the NSF and NIH have data sharing policies in
their grant guidelines to prevent sharing personally identifiable information,
and to anonymize data on human subjects.

In small datasets, a hashing scheme is enough to anonymize minimal personal
information. Make sure to not store the hashing scheme with the data to prevent
inadvertent sharing and don't use a commonplace hashing technique. Famously, New
York City officials shared what they thought was anonymized data on cab drivers
and over 173 million cab rides. However, it was quickly recognized that the city
anonymized the data with a simple MD5 hashing scheme and all 20 GB of data was
de-anonymized in a matter of hours [@Goodin]. In more problematic cases, the
data itself allows identifiability: this is the case with human genomic data
that map directly onto a subject's identity [@Homer2008]. Methods for dealing
with these complex issues at the intersection of data storage and privacy are
rapidly evolving, and include storing changes against a reference genome to help
with privacy and data volume [@Kahn2011, @wandelt2014trends], or bringing
computation to data storage facilities instead of vice versa [@Gaye2014]. Having
a plan for privacy before data acquisition is important, because it can
determine or limit how data will be stored.

# Rule 8: Have a systematic backup scheme {-}

Every storage medium can fail, and every failure can result in loss of data.
Researchers should therefore back data up at all stages of the research process.
Data stored on local computers or institutional servers during the collection
and analysis phases should be backed up to other locations and formats to
protect against data loss. No backup system is failsafe (see the stories of the
[Dedoose crash][dedoose] and the [near deletion of Toy Story 2][ts2]), so more
than one backup system should be used. Kristin Briney advocates the "[Rule of
3](http://dataabinitio.com/?p=320)" for backing up data: two onsite copies (such
as on a computer, an external hard drive, or a tape) and one offsite copy (e.g.
in cloud storage). Keeping backups in multiple locations protects against data
loss due to theft, natural disasters, etc.

[dedoose]: https://www.insidehighered.com/news/2014/05/16/dedoose-crash-shows-dangers-handing-data-cloud-services
[ts2]: http://thenextweb.com/media/2012/05/21/how-pixars-toy-story-2-was-deleted-twice-once-by-technology-and-again-for-its-own-good/

Researchers should also test their backups regularly to ensure that they are
functioning properly. Common reasons for backup failure include:

 - faulty backup software
 - incorrect configuration (e.g., not backing up sub-directories)
 - encryption (e.g., someone has encrypted the backups but lost the
   password)
 - media errors

Consider the backup plan of your selected data repository before publishing your
data. Many repositories mirror the data they host on multiple machines. If
possible, find out about the long-term storage plans of the repository. Are
there plans in place to keep data available if the organization that manages the
repository dissolves?

# Rule 9: The location and method of data storage depends on how much you have. {-}

The storage method you should choose depends on the size and nature of your
data; the cost of storage, the time it takes to transfer the data, how the data
will be used and any privacy concerns. Data is increasingly generated in the
range of many terabytes by environmental sensors, satellites, automated
analytical tools, simulation models, and genomic sequencers. Even larger data
generating machines like the Large Hadron Collider (LHC) and the Large Scale
Synoptic Survey Telescope (LSST) generate many TBs per day, rapidly accumulating
to PB scale over the course of any particular study. While the cost of storage
continues to decrease, the volume of data to be stored impacts the choice of
storage methods and locations: for large datasets it is necessary to balance the
cost of storage with the time of access and costs of re-generating the data.

When data takes too long to transfer or is costly to store, it can become more
efficient to use a computer that can directly access and use the data in place.
Inactive data can be put in longer-term storage; this is less expensive, but can
take longer to retrieve. Some storage systems automatically migrate 'stale'
files to longer term storage. Alternatively, some computing can be done 'in the
database' or 'on disk' via database query languages (e.g. SQL, MapReduce) that
perform basic arithmetic or via the use of procedural languages (e.g. R, Python,
C) embedded in the database server. Modern database technologies such as HDFS
and Spark allow these computations to be done on data of almost any size. When
data is larger than RAM, it can be handled by a 'big memory' node, which most
high-performance computing have deployed -- relying on tight software/hardware
integration, these are currently around 1-4 TB. This allows the user to read in
and use a large dataset without special tools.

If you regularly only need access to a small subset of your data or need to
share it with many collaborators, a web based API might be a good solution.
Using this method, many users can send requests via HTTP to a web service which
can subset the data, perform in database computation, and return smaller volumes
of data as specific slices. Tools based on web services make it easier to find
and download data, and facilitate analysis via reproducible scripts, however
they can lead to excessive and careless abuse of resources. The time required to
re-download and recompute results can be reduced by 'caching'. Caching stores
copies of downloads and generated files that are recognized when the same script
is run multiple times.

# Rule 10: Data should be stored in a machine readable-format {-}

Not only data should be stored in an open format, to ensure that it will be
easily and widely accessible (Rule 4), but data should also be stored in a
format that computers can easily make use of.

As datasets become larger, it is crucial that they can be parsed efficiently.
This is best achieved by using standard data formats that have clear
specifications (e.g., CSV, XML, JSON, HDF5), or by using databases. Such data
formats can be handled by a variety of programming languages, as efficient and
well-tested libraries for parsing them are typically available. These standard
data formats also ensure interoperability, facilitate re-use, and reduce the
chances of data loss or mistakes being introduced during conversion between
formats.

When data can be easily imported into familiar software, whether it be a
scripting language, a spreadsheet, or any other computer program that can import
these common files, data become easier to re-use. Computer source code: the
human readable software code that uses data, provide meta-data as well, making
the analysis more transparent, such that all assumptions are implicitly stated
in a human readable script. This also enables extraction of the analyses
performed, their reproduction, and their modification. This principle is
exemplified by the scripts used to import allometric measurements into the BAAAD
database.

<!-- NZ comment: Citation (and perhaps more explanation) needed -->

To take full advantage of data, it can be useful for it to be structured in a
way that make manipulation and analysis easy. One such structure for data has
been named *tidy* data [@Wickham2014tidy].
Technically known as the 'third normal form',<!-- (was it third? see
@hadley's comments on this rule in github issue.--> each variable is a
column, each observation is a row, and each type of observational unit
is a table. <!-- this is not true for large, multidimensional data in
which dimensions (date, time) are stored in a different way from other
variables --> When data is organized in this way, the duplication of
information is reduced and it is easier to subset or summarize the
dataset to include the variables or observations of interest.

<!-- include figure that shows example of untidy and equivalent tidy data? -->

Interoperability is facilitated when variable names are mapped to
existing data standards. For instance, for biodiversity data, the
[Darwin Core Standard](http://www.tdwg.org/standards/450/) provides a
set of terms that describe observations, specimens, samples, and
related information for a taxa. Because each term is clearly defined
and documented, each dataset can use the terms consistently,
facilitating data sharing across institutions, applications, and
disciplines.

With machine-readable data, it is also easier to build an Application
Programming Interface (API) to query the dataset to retrieve a subset
of interest. <!-- NZ comment: An important point, and perhaps worth
spending a few more sentences on? -->

# Conclusions {-}

# Acknowledgements {-}

National Center for Supercomputing Applications.
Software Carpentry Foundation.
iDigBio/NSF.

# Figure Legends {-}

Figures here:  Will need to figure out numbering...

# Tables {-}

Tables here:  Will need to figure out numbering...

\nolinenumbers

# References {-}
\bibdata{resources/manuscript.bib}
