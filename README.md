#CaboLabs EHRServer

## Service-oriented clinical data repository for shared EHRs/EMRs/PHRs based on the [openEHR standard](http://openehr.org).

### Main Services:

* clinical data commit
* clinical data query (with aggregation and grouping capabilities)
* data synchronization (for backup and server clustering)


### Features:

* multiformat XML/JSON
* web services (REST and SOAP)
* versioned openEHR objects
* data indexing


### Main functionalities:

* Patient management
* EHR and contributions management
* Query building and testing
* Usage logs


## The project

### Intended audience

* Clinical Record Managers
* EHR/EMR/PHR System Admins
* Healthcare Informatics Trainers & Students


### Technologies

* [Grails Framework](http://grails.org)
* [Groovy](http://groovy.codehaus.org)
* [Java](http://docs.oracle.com/javase/specs)


### Out of scope

* EHR/EMR/PHR apps should be written separately as clients of the EHRServer, but use the provided data services to access and send data from/to the EHRServer.
* Data analysis, data aggregation, business intelligence and other data processing related applications should be written separately from the EHRServer, all those systems can get data from the EHRServer using the provided data services.


### Milestones and deliverables

#### M1. Basic services in XML and JSON and internal operations

* list and show of EHRs, Compositions, Queries and Contributions (85% done)
* commit reception (just openEHR XML for now) (95% done)
* data indexing operation (90% done)
* openEHR archetype definition indexing (0% done)


#### M2. GUI to manage internal data (list, show, create, edit, delete)

* EHR management (40%)
* Directory management (0%)
* Composition management
* Query management
* Contribution management
* Patient management (should be externalized to a demographic server)
* User management (0%)


#### M3. Advanced features (each one could be a milestone itself)

* Support rules for directory management (copying and moving compositions between folders)
* Composition versioning
* Persistent composition support
* Querying versioned objects
* Data syncrhonization between servers
* Support for AQL/EQL output (openEHR archetype-based query language)


## REST API
### Get EHRs
/rest/ehrList(String format:XML|JSON, int max, int offset)

### Get patients (this service will be obsolete when we move patient data to a specific demographic repo)
/rest/patientList(String format:XML|JSON, int max, int offset)

### Get EHR for a subject
/rest/ehrForSubject(String subjectUid, String format:XML|JSON)

### Get EHR by uid
/rest/ehrGet(String ehrUid, String format:XML|JSON)

### Get all compositions for a patient
/rest/findCompositions(String ehrId)

### Get query definitions
/rest/queryList(String format:XML|JSON, int max, int offset)

### Query execution by uid
/rest/query(String queryUid, String ehrId)

### Commits a set of clinical documents to the EHR (not implemented yet)
/rest/commit(String ehrUid, Collection<Composition> versions)

