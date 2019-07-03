# fdev Project

Skynet-CLI dependency and Skynet Maven plugin allow you to perform the following functionalities:

* Initializes your ingestion and schema files.
* Deploys your files in Bitbucket,
* Executes a Kirby job (or another Spark job) in your local machine.
* Executes a Feature job in your local machine.
* Reads a path containing Avro or Parquet files to show the content of those files.


If you want to use Skynet features, you can use **skynet-cli** module through IntelliJ configuration or
**skynet-maven-plugin** through the command line.


1. Add new Run/Debug Configuration of type Application (in the Run menu).
2. Set ``com.datio.skynet.cli.SkynetCli`` as the main class.
3. Set ``fdev-ingestion/fdev`` as working directory.
4. Set ``fdev`` in "Use classpath of module" option.
5. Fill "Program arguments" field with the action and arguments you want (arguments for each step are 
detailed below):

    1. Initialize your TPT files: ``init-tpt``.
    2. Initialize your ingestion files: ``init``.
    3. Initialize your schema files: ``init-schemas``.
    4. Initialize all the schema files: ``init-all-schemas``.
    5. Initialize your DQ files: ``init-dq``.
    6. Initialize all your DQ files: ``init-all-dq``.
    7. Deploy your TPT, schemas, ingestion and data quality files in Git and create a PR: ``deploy``.
    8. Change to another Git branch: ``go-to``
    9. Run local Kirby jobs: ``run-kirby``.
    10. Run local Feature jobs: ``run-feature``.
    11. Run local Spark jobs: ``run-job``.
    12. Read files containing Avro or Parquet files in a directory: ``read-path``.
    13. Generate and fill the required tabs to import the data dictionary in Sophia: ``sophia-tabs``.
    14. Fill the tab with the MVP rules defined for data quality: ``dq-mvp``.
    
NOTE: when creating the project via the archetype, you will have in the root folder a folder named ``runConfigurations``.
If you copy this folder into the ``.idea`` folder (after creating the project in IntelliJ) and reopen the project,
you'll get all configurations already done. 
    

Same functionalities listed above can be executed using Maven. To run Skynet commands with Maven,
just run the Maven command (inside of the ``fdev`` submodule or with -pl ``fdev`` option)
followed by the goal you want to execute:
    
 1. Initialize your TPT files: ``mvn skynet:initTpt``.
 2. Initialize your ingestion files: ``mvn skynet:init``.
 3. Initialize only your schema files: ``mvn skynet:initSchemas``.
 4. Initialize all your schema files: ``skynet:initAllSchemas``.
 5. Initialize your DQ files: ``skynet:initDq``.
 6. Deploy your ingestion files and create DataProc jobs: ``mvn skynet:deploy``.
 7. Deploy your schema files in Nexus/Artifactory: ``mvn skynet:deploySchemas``.
 8. Deploy all your schema files in Nexus/Artifactory: ``mvn skynet:deployAllSchemas``.
 9. Deploy your DQ files and create DataProc jobs: ``mvn skynet:deployDq``.
 10. Create a Spark job in DataProc: ``mvn skynet:createSparkJob``.
 11. Run local Kirby jobs: ``mvn skynet:runKirby``.
 12. Run local Feature jobs: ``mvn skynet:runFeature``.
 13. Run local Spark jobs: ``mvn skynet:runJob``.
 14. Read a path containing Avro or Parquet files: ``mvn skynet:readPath``.
 15. Run ingesion DataProc jobs: ``mvn skynet:ingest``.
 16. Ingestion validation through the Spark validation job: ``mvn skynet:ingest -Dtest=true``.
 17. Verify conf and JSON files: ``mvn skynet:verify``.
 18. Verify schema files: ``mvn skynet:verifySchemas``.
 19. Verify schema files: ``mvn skynet:verifyTpt``.
 20. Verify DQ files: ``mvn skynet:verifyDq``.
 21. Report deployment status: ``mvn skynet:report<option>``.
 22. Use admin options (see help Maven command) ``mvn skynet:admin-<option>``.
 23. Get **skynet-maven-plugin** help and usage: ``mvn skynet:help``.
