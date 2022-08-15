# Example 03: FHIR 

The patient is referenced as the subject of DiagnosticReport,DocumentReference, ImagingStudy or ImagingSelection. Mapping to DICOM is as follows:

| FHIR attribute                           | Attribute Name                | TAG         | VR | Value                                                       |
| ---------------------------------------- | ----------------------------- | ----------- | -- | ----------------------------------------------------------- |
| Patient.name.use=official                | Patient's Name                | (0010,0010) | PN | Smith\^John^^^                                              |
| Patient.gender                           | Patient's Sex                 | (0010,0040) | CS | F                                                           |
|                                          | Gender Identity Sequence      | (0010,xxxx) | SQ |                                                             |
| Patient.genderIdentity.value             | \>Gender Code                 | (0010,xxx4) | SQ |                                                             |
| code                                     | \>\>Code Value                | (0008,0100) | SH | 446151000124109                                             |
| system                                   | \>\>Coding Scheme Designator  | (0008,0102) | SH | SCT                                                         |
| display                                  | \>\>Code Meaning              | (0008,0104) | LO | Identifies as male gender                                   |
| Patient.genderIdentity.period            | \>Validity Period sequence    | (0010,xxx5) | SQ |                                                             |
| start                                    | \>\>Start DateTime            | (0010,xxx6) | DT | 20220715010000                                              |
| end                                      | \>\>Stop DateTime             | (0010,xxx7) | DT |                                                             |
|                                          | \>Gender Comment              | (0010,xxx8) | LT |                                                             |
|                                          | Sex Comment                   | (0010,xxx1) | LT |                                                             |
|                                          | Sex for Clinical Use Sequence | (0010,xxx2) | SQ |                                                             |
| serviceRequest.sexForClinicalUse.value   | \>SFCU Code Sequence          | (0010,xxx9) | SQ |                                                             |
| code                                     | \>\>Code Value                | (0008,0100) | SH | 248152002                                                   |
| system                                   | \>\>Coding Scheme Designator  | (0008,0102) | SH | SCT                                                         |
| display                                  | \>\>Code Meaning              | (0008,0104) | LO | Female                                                      |
| serviceRequest.sexForClinicalUse.period  | \>Validity Period sequence    | (0010,xxx5) | SQ |                                                             |
| start                                    | \>\>Start DateTime            | (0010,xxx6) | DT | 20220715090000                                              |
| end                                      | \>\>Stop DateTime             | (0010,xxx7) | DT |                                                             |
| serviceRequest.sexForClinicalUse.comment | \>SFCU Comment                | (0010,xxx1) | LT | Hormonal treatment, use affirmed gender Cr reference ranges |
|                                          | \>SFCU Reference              | (0010,xx10) | UR |                                                             |
|                                          | Person Names to Use Sequence  | (0010,xxx3) | SQ |                                                             |
| Patient.name.use=usual                   | \>Name to use                 | (0010,xx12) | LT | John Smith                                                  |
|                                          | \>Validity Period Sequence    | (0010,xxx5) | SQ |                                                             |
|                                          | \>\>Start DateTime            | (0010,xxx6) | DT |                                                             |
|                                          | \>\>Stop DateTime             | (0010,xxx7) | DT |                                                             |
|                                          | \>Name to Use Comment         | (0010,xx13) | LT |                                                             |
| Patient.gender (based on local mapping)  | Sex at Birth Code Sequence    | (0010,xx25) | CS | F                                                           |
|                                          | \>\>Code Value                | (0008,0100) | SH | 248152002                                                   |
|                                          | \>\>Coding Scheme Designator  | (0008,0102) | SH | SCT                                                         |
|                                          | \>\>Code Meaning              | (0008,0104) | LO | Female                                                      |
