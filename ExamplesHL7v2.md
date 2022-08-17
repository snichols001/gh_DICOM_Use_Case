# Example 01: Imaging Order

Below is a HL7 v2.9.1 OMI Imaging Order for the [DICOM Use Case](http://build.fhir.org/ig/HL7/fhir-gender-harmony/branches/main/dicom_use_case.html).

```
MSH|^~\&|||||20220715090000||OMI^O23|WSA5mY0UBuCGrytRTAFR8UWJ|P|2.9.1
PID|||patientID^^^^MR||Smith^Janet^^^^^B~Smith^John^^^^^D|||F
GSP|1|S||76691-5^Gender identity^LN|446151000124109^Identifies as male gender^SCT|20220715090000  
GSC|1|S||248152002^Female^SCT|20220715090000|OBR^4||Hormonal treatment, use affirmed gender Cr reference ranges
ORC|NW||||||||20220715090000|||^Cure^Matt^^^^MD
OBR|1|entityID|fillrtOrderNum|82800-4^PET+CT Heart W contrast IV^LN||||||||||||||||||||NMS|||||||^Reason for Study|
IPC|accessionNum|procedureID|studyInstanceUID|schProcedureStepId|PT^Positron emission tomography^DCM|122793^PET Myocardial Perfusion, Rest and Stress^DCM
```

This maps to DICOM Modality Worklist as follows:

| V2                                   | Attribute Name                | Tag         | VR | Value                                                       |
| ------------------------------------ | ----------------------------- | ----------- | -- | ----------------------------------------------------------- |
| PID-5 Name Type Code = Birth Name    | Patient's Name                | (0010,0010) | PN | Smith\^Janet^^^                                             |
| PID-8                                | Patient's Sex                 | (0010,0040) | CS | F                                                           |
|                                      | Patient’s Gender              | (0010,xxxx) | CS | M                                                           |
|                                      | Gender Identity Sequence      | (0010,xxxx) | SQ |                                                             |
|                                      | \>Gender Code Sequence        | (0010,xxx4) | SQ |                                                             |
| GSP-5-1                              | \>\>Code Value                | (0008,0100) | SH | 446151000124109                                             |
| GSP-5-3                              | \>\>Coding Scheme Designator  | (0008,0102) | SH | SCT                                                         |
| GSP-5-2                              | \>\>Code Meaning              | (0008,0104) | LO | Identifies as male gender                                   |
|                                      | \>Validity Period sequence    | (0010,xxx5) | SQ |                                                             |
|                                      | \>\>Start DateTime            | (0010,xxx6) | DT |                                                             |
|                                      | \>\>Stop DateTime             | (0010,xxx7) | DT |                                                             |
|                                      | \>Gender Comment              | (0010,xxx8) | LT |                                                             |
|                                      | Sex Comment                   | (0010,xxx1) | LT |                                                             |
|                                      | Sex for Clinical Use Sequence | (0010,xxx2) | SQ |                                                             |
|                                      | \>SFCU Code Sequence          | (0010,xxx9) | SQ |                                                             |
| GSC-4-1                              | \>\>Code Value                | (0008,0100) | SH | 248152002                                                   |
| GSC-4-3                              | \>\>Coding Scheme Designator  | (0008,0102) | SH | SCT                                                         |
| GSC-4-2                              | \>\>Code Meaning              | (0008,0104) | LO | Female                                                      |
|                                      | \>Validity Period sequence    | (0010,xxx5) | SQ |                                                             |
|                                      | \>\>Start DateTime            | (0010,xxx6) | DT | 20220715090000                                              |
|                                      | \>\>Stop DateTime             | (0010,xxx7) | DT |                                                             |
| GSC-8                                | \>SFCU Comment                | (0010,xxx1) | LT | Hormonal treatment, use affirmed gender Cr reference ranges |
|                                      | \>SFCU Reference              | (0010,xx10) | UR |                                                             |
|                                      | Person Names to Use Sequence  | (0010,xxx3) | SQ |                                                             |
| PID-5 Name Type Code = Customary     | \>Name to use                 | (0010,xx12) | LT | Smith, John                                                 |
|                                      | \>Validity Period Sequence    | (0010,xxx5) | SQ |                                                             |
|                                      | \>\>Start DateTime            | (0010,xxx6) | DT | 20220715090000                                              |
|                                      | \>\>Stop DateTime             | (0010,xxx7) | DT |                                                             |
|                                      | \>Name to Use Comment         | (0010,xx13) | LT |                                                             |
| PID-8 (based on local mapping rules) | Sex at Birth Code Sequence    | (0010,xx25) | CS | F                                                           |
|                                      | \>\>Code Value                | (0008,0100) | SH | 248152002                                                   |
|                                      | \>\>Coding Scheme Designator  | (0008,0102) | SH | SCT                                                         |
|                                      | \>\>Code Meaning              | (0008,0104) | LO | Female                                                      |

# Example 02: Patient Name Update

Below is a HL7 v2.9.1 ADT Demographics Update for the DICOM Use Case.

```
MSH|^~\&|||||20220715010000||ADT^A08|TwxxneTRWE9JGX4U2p3h|P|2.9.1
EVN||20220715151118||01
PID|||patientID^^^^MR||Smith^John^^^^^D~Smith^Janet^^^^^NOUSE|||F|
GSP|1|S||76691-5^Gender identity^LN|446151000124109^Identifies as male gender^SCT|20220715010000
PV1||O
```

Note: in previous v2 versions, the first occurrence indicated the legal name. In this case, the Customary name is listed first for legacy compatibility.


This maps to DICOM Modality Worklist as follows:

| V2                                   | Attribute Name                | Tag         | VR | Value                                                       |
| ------------------------------------ | ----------------------------- | ----------- | -- | ----------------------------------------------------------- |
| PID-5 Name Type Code = Customary     | Patient's Name                | (0010,0010) | PN | Smith\^John^^^                                              |
| PID-8                                | Patient's Sex                 | (0010,0040) | CS | F                                                           |
|                                      | Patient’s Gender              | (0010,xxxx) | CS | M                                                           |
|                                      | Gender Identity Sequence      | (0010,xxxx) | SQ |                                                             |
|                                      | \>Gender Code Sequence        | (0010,xxx4) | SQ |                                                             |
| GSP-5-1                              | \>\>Code Value                | (0008,0100) | SH | 446151000124109                                             |
| GSP-5-3                              | \>\>Coding Scheme Designator  | (0008,0102) | SH | SCT                                                         |
| GSP-5-2                              | \>\>Code Meaning              | (0008,0104) | LO | Identifies as male gender                                   |
|                                      | \>Validity Period sequence    | (0010,xxx5) | SQ |                                                             |
|                                      | \>\>Start DateTime            | (0010,xxx6) | DT | 20220715010000                                              |
|                                      | \>\>Stop DateTime             | (0010,xxx7) | DT |                                                             |
|                                      | \>Gender Comment              | (0010,xxx8) | LT |                                                             |
|                                      | Sex Comment                   | (0010,xxx1) | LT |                                                             |
|                                      | Sex for Clinical Use Sequence | (0010,xxx2) | SQ |                                                             |
|                                      | \>SFCU Code  Sequence         | (0010,xxx9) | SQ |                                                             |
| GSC-4-1                              | \>\>Code Value                | (0008,0100) | SH | 248152002                                                   |
| GSC-4-3                              | \>\>Coding Scheme Designator  | (0008,0102) | SH | SCT                                                         |
| GSC-4-2                              | \>\>Code Meaning              | (0008,0104) | LO | Female                                                      |
|                                      | \>Validity Period sequence    | (0010,xxx5) | SQ |                                                             |
|                                      | \>\>Start DateTime            | (0010,xxx6) | DT |                                                             |
|                                      | \>\>Stop DateTime             | (0010,xxx7) | DT |                                                             |
| GSC-8                                | \>SFCU Comment                | (0010,xxx1) | LT | Hormonal treatment, use affirmed gender Cr reference ranges |
|                                      | \>SFCU Reference              | (0010,xx10) | UR |                                                             |
|                                      | Person Names to Use Sequence  | (0010,xxx3) | SQ |                                                             |
|                                      | \>Name to use                 | (0010,xx12) | LT |                                                             |
|                                      | \>Validity Period Sequence    | (0010,xxx5) | SQ |                                                             |
|                                      | \>\>Start DateTime            | (0010,xxx6) | DT | 20220715009000                                              |
|                                      | \>\>Stop DateTime             | (0010,xxx7) | DT |                                                             |
|                                      | \>Name to Use Comment         | (0010,xx13) | LT |                                                             |
| PID-8 (based on local mapping rules) | Sex at Birth Code Sequence    | (0010,xx25) | CS | F                                                           |
|                                      | \>\>Code Value                | (0008,0100) | SH | 248152002                                                   |
|                                      | \>\>Coding Scheme Designator  | (0008,0102) | SH | SCT                                                         |
|                                      | \>\>Code Meaning              | (0008,0104) | LO | Female                                                      |

# Example 05: Imaging Report

Below is a HL7 v2.9.1 Unsolicited Observation Result containing the
Imaging Report narrative.

```
MSH|^~\&|||||20220715142240||ORU^R01|WSA5mY0UBuCGrytRTAFR8UWJ|P|2.9.1
PID|||patientID^^^^MR||Smith^John^^^^^D|||F|
GSP|1|S||76691-5^Gender identity^LN|446151000124109^Identifies as male gender^SCT
GSC|1|S||248152002^Female^SCT||OBR^4||Hormonal treatment, use affirmed gender Cr reference ranges
ORC|CN||||||||20220715090000|||^Cure^Matt^^^^MD
OBR|1|accessionNum||82800-4^PET+CT Heart W contrast IV^LN|||20220715110000||||
OBX|1|CWE|55111-9^Current Imaging Procedure Description^LN||Imaging technique (protocol, contrast, radiotracer) described here||||||F|
OBX|2|CWE|19005-8^Impression^LN||Report narrative goes here||||||F|
OBX|3|CWE|55110-1^Conclusion^LN||Conclusion goes here||||||F|
```

*OBX Segments containing Imaging Report Narrative omitted for Brevity*