# Example 04: CDA Release 2 Imaging Report

Examples are adopted from [HL7 examples](http://hl7-c-cda-examples.herokuapp.com/search).

Patient demographics in the CDA header are as follows:
```
<recordTarget>
	<patientRole>
		<id root="1.2.840.113619.2.62.994044785528.10" extension="0000680029"/>
		<addr nullFlavor="NI"/>
		<telecom nullFlavor="NI"/>
		<patient>
			<name>
				<given>John</given>
				<family>Smith</family>
			</name>
			<administrativeGenderCode codeSystem="2.16.840.1.113883.5.1"code="F"/>
			<birthTime value="19641128"/>
		</patient>
	</patientRole>
</recordTarget>
```
The Patient's Gender information is included in Social History:
```
<component>
	<section>
		<templateId root="2.16.840.1.113883.10.20.22.2.17" extension="2015-08-01"/>
		<templateId root="2.16.840.1.113883.10.20.22.2.17"/>
		<code code="29762-2" codeSystem="2.16.840.1.113883.6.1" codeSystemName="LOINC"/>
		<title>Social History</title>
		<text>
						The patient was born female and identifes as male and is currently undergoing gender affirming hormone therapy.
			<table>
				<thead>
					<tr>
						<th>Obs</th>
						<th>Value</th>
					</tr>
				</thead>
				<tbody>
					<tr>
						<td ID="gender_narrative1">Gender Identity</td>
						<td ID="gender_value1">Identifies as male gender</td>
					</tr>
					<tr>
						<td ID="sex_narrative">Sex Assigned at Birth</td>
						<td ID="sex_value">Female</td>
					</tr>
				</tbody>
			</table>
		</text>
		<entry>
			<observation classCode="OBS" moodCode="EVN">
				<templateId root="2.16.840.1.113883.10.15.4" extension="2022-09-01" /> <!-- from Trifolia? -->
				<code code="76691-5" codeSystem="2.16.840.1.113883.6.1" displayName="Gender Identity"/>
				<text>
					<reference value="#gender_narrative1"/>
				</text>
				<statusCode code="complete"/>
				<value xsi:type="CD" codeSystem="2.16.840.1.113883.6.96" codeSystemName="SNOMED CT" code="446151000124109" displayName="Identifies as male gender">
					<originalText>
						<reference value="#gender_value1"/>
					</originalText>
				</value>
			</observation>
		</entry>
		<entry>
			<observation classCode="OBS" moodCode="EVN">
				<templateId root="2.16.840.1.113883.10.20.22.4.200" extension="2016-06-01"/>
				<code code="76689-9" codeSystem="2.16.840.1.113883.6.1" displayName="Sex Assigned At Birth"/>
				<text>
					<reference value="#sex_narrative"/>
				</text>
				<statusCode code="completed"/>
				<value xsi:type="CD" codeSystem="2.16.840.1.113883.6.96" codeSystemName="SNOMED CT" code="20220715009000" displayName="Female">
					<originalText>
						<reference value="#sex_value"/>
					</originalText>
				</value>
			</observation>
		</entry>
	</section>
</component>
```
SFCU is included in the Procedure Description:
```
<component>
	<section classCode="DOCSECT" moodCode="EVN">
		<templateId root="1.2.840.10008.9.3"/>
		<id root="1.2.840.10213.2.62.9940434234785528.11428954534542805"/>
		<code code="55111-9" codeSystem="2.16.840.1.113883.6.1" codeSystemName="LOINC" displayName="Current Imaging Procedure Description"/>
		<title>Imaging Procedure Description</title>
		<text>
			<table>
				<tbody>
					<tr>
						<td ID="gender_narrative2">Sex For Clinical Use</td>
						<td ID="gender_value2">Female</td>
					</tr>
					<tr>
						<td ID="Technique1">Imaging Technique</td>
						<td ID="Technique1OriginalText">The patient is a transgender male, undergoing hormonal treatment. Based on physician instructions, affirmed gender creatinine reference ranges were confirmed to be within normal values prior to the administration of non-ionic iodinated contrast agent.. CT images for attenuation correction and anatomic localization followed by PET images were obtained..</td>
					</tr>
				</tbody>
			</table>
		</text>
		<entry>
			<observation classCode="OBS" moodCode="EVN">
				<templateId root="2.16.840.1.113883.10.15.3" extension="2022-09-01"/>
				<code code="99501-9" codeSystem="2.16.840.1.113883.6.1" displayName="Sex for clinical use"/>
				<text>
					<reference value="#gender_narrative2"/>
				</text>
				<statusCode code="complete"/>
				<value xsi:type="CD" codeSystem="2.16.840.1.113883.6.96" codeSystemName="SNOMED CT" code="20220715009000" displayName="Female">
					<originalText>
						<reference value="#gender_value2"/>
					</originalText>
				</value>
				<entryRelationship typeCode="SPRT">
					<act classCode="ACT" moodCode="EVN">
						<templateId root="2.16.840.1.113883.10.20.22.4.122" />
						<code code="NP" displayName="https://academic.oup.com/jes/article/5/Supplement\_1/A790/6241237"/>
					</act>
				</entryRelationship>
				<entryRelationship typeCode="REFR">
					<procedure classCode="SUBST" moodCode="EVN">
						<code code="82800-4" codeSystem="2.16.840.1.113883.6.1" displayName="PET+CT Heart W contrast IV" />
					</procedure>
				</entryRelationship>
			</observation>
		</entry>
	</section>
</component>
```

