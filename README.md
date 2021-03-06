## mtf-ensit-datatype
mtf-ensit-datatype takes a [ <a href="https://www.niem.gov/technical/Pages/niem.aspx" target="_blank">NIEM-based</a> ] approach for describing a NIEM-conformant XML representation of the MIL-STD-6040 USMTF messages ENSIT and EOBSREP.

Start with 

    ./readme.html
    
after downloading and expanding the zip file provided by GitHub.

To clone this repository, download [ <a href="https://git-scm.com" target="_blank">git</a> ] first, if you don't already have it.

Then, with git installed, enter the following in a target directory:

    git clone https://github.com/gmoyanollc/mtf-ensit-datatype.git

    
#USMTF ENSIT and EOBSREP
MIL-STD-6040 USMTF messages ENSIT (Enemy Situational Awareness) and EOBSREP (Enemy Observation Report) are base messages for a USA SIGACT (Significant Activity) message supported by [ <a href="https://marinecorpsconceptsandprograms.com/programs/command-and-controlsituational-awareness-c2sa/tactical-service-oriented-architecture-tsoa" target="_blank">USMC MC2SA TSOA</a> ], a sponsor of this effort.

#USA SIGACT to USMTF
SIGACT is a message data type implemented by USA C2 systems. CPOF is one of those systems.  Since USA is the sole steward of the SIGACT data type, it can be argued that the data type is proprietary to USA.  In contrast, USMTF is a Joint Staff, Military Services defined specification for C2 messages.  Its stewardship is on-going and collaborated upon by Joint Staff and Military Services.  

mtf-ensit-datatype transforms SIGACT messages to a NIEM-conformant XML representation of the MIL-STD-6040 USMTF messages ENSIT and EOBSREP.  Transformations are possible by mapping data components between a data types.  

The following diagram depicts an example transformation from a SIGACT instance to a mtf-ensit-datatype instance:

            /------------\    /--------------------------------\
            |   SIGACT   |    |  Sigact-to-mtf-ensit-datatype  |
            |  instance  |    |        XSL instructions        |
            \------------/    \--------------------------------/
                    \              /
                     |             |
                     V             V
                  /-------------------\
                 /     Transformer     \
                /        service        \
                \-----------------------/
                            |
                            V
                 /----------------------\
                 |  mtf-ensit-datatype  |
                 |       instance       |
                 \----------------------/
                    
Ultimately, if USMTF authoritative "slash-dash" is required, a transformation may follow that creates a MTF "slash-dash" instance:

    /----------------------\    /---------------------------------------\
    |  mtf-ensit-datatype  |    |  mtf-ensit-datatype-to-mtf.slashdash  |
    |       instance       |    |            XSL instructions           |
    \----------------------/    \---------------------------------------/
                       \              /
                        |             |
                        V             V
                     /-------------------\
                    /     Transformer     \
                   /        service        \
                   \-----------------------/
                               |
                               V
                      /-----------------\
                      |  mtf.slashdash  |
                      |    instance     |
                      \-----------------/
                      
The same may be true for producing a USMTF authoritative XML-MTF instance.

#Developer "Friction"
This work strives to alleviate the "friction" that often times is experienced by software developers when only XML Schema files are provided.  

In addition to XML Schema files and documentation, the following capabilities and artifacts are included in this work product:

            *  Git repository
            *  Ant and Maven-driven test, build, and packaging automation
            *  XSL 3.0 XML and JSON data format transformations
            *  XSL Schematron build and application rule validation
            *  USMTF-XML componentization and classification
            *  Exploratory RDF gleaning of relevant things and facts (triples)

A software developer can therefore deploy, exercise, and reuse this product in their own development environment.  

Example benefits to a software developer are the following:

            *  Testing tasks may be reused to troubleshoot and validate a configuration
            *  Validation and transformation instructions should ease and expedite development
            *  Sample results may be compared with development and integration results
            *  Artifacts and transformations may be reused to update mtf-ensit-datatype from a new version of USMTF-XML.
            *  Exploratory work in RDF gleaning may bootstrap other efforts to describe and extract relevant things and facts (triples) from information exchange instances.
                
Implementing a familiar Maven file structure, most of the artifacts are found under the folder: 

    ./src/main/resources 

The folders within [ ./src/main/resources ] contain XML Schema files and sample instances, message data component mappings, validation and transformation instruction files, and development resources and tests.  The structure closely resembles the sample NIEM MPD folder structure described in [ <a href="http://reference.niem.gov/niem/specification/model-package-description/3.0/model-package-description-3.0.html#appendix_E" target="_blank">NIEM Model Package Description Specification</a> ].
        
Documentation is contained in the [ ./src/main/resources/documentation ] folder.  Readme files are also contained in folders enhanced by specific instructions.

#Authoritative Sources
This complete work is maintained on Software Forge.mil at project [ <a href="https://software.forge.mil/sf/projects/magtf_c2" target="_blank">USMC - MAGTF C2</a> ] SVN repo [ <a href="https://svn.forge.mil/svn/repos/soimessaging/TsoaInformationModel/DataFormat/mtf-ensit-datatype" target="_blank">SoiMessaging</a> ].  A subset of the work is on GitHub at [ <a href="https://github.com/gmoyanollc/mtf-ensit-datatype" target="_blank">gmoyanollc/mtf-ensit-datatype</a> ] .

This work is derived from authoritative MIL-STD-6040 USMTF XML work maintained on Software Forge.mil at project [ <a href="https://software.forge.mil/sf/projects/mtfxml" target="_blank">MTF XML</a> ].  A subset of the work is also on GitHub at [ <a href="https://github.com/mil-oss/MTFXML" target="_blank">Mil-OSS/MTFXML</a> ] .

A version of the MIL-STD-6040 USMTF description and specification is available at Department of Defense [ <a href="http://quicksearch.dla.mil/qsDocDetails.aspx?ident_number=214270" target="_blank">Quick Search ASSIST</a> ].
