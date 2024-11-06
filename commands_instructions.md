
# Commands and Instructions

### Teleport Commands
```bash
tsh ls
tsh ssh teleport_user@staging.insight.processor.12
```

### AWS S3 Download
```bash
aws s3 cp --recursive s3://uc.analytics/production/apollo/TEST/ALYA-739/{entity_type}/{state_code}/20240912/normal/ /home/teleport_user/data/{entity_type}/{state_code}/20240912/normal/
```

### Zip and SCP Commands
```bash
cd /home/teleport_user/data/{entity_type}/
zip -r {state_code}.zip {state_code}/
tsh scp teleport_user@staging.insight.processor.12:/home/teleport_user/data/{entity_type}/{state_code}.zip /home/mis/norm/{entity_type}/
```

### Git Commands
```bash
git checkout experimental
git pull upstream experimental
git checkout -b {ticket_number}
git pull divya ALYA-718

git status
git add {file_path}
git commit -m "{message}"
git branch -b {ticket_number}
git push origin {ticket_number}

cd internprathviraj/a-norm/

git checkout experimental
git pull upstream experimental
git checkout {ticket_number}
git pull origin {ticket_number}
```

### Gradle and Java Commands
```bash
cd normalisation/
gradle BI --refresh-dependencies

cd ..
cd output_jar

java -jar -Xms20G  MultiNormIncremental.jar -seeddir ~/data/{entity_type}/{state_code}/20240912/normal/seed/ -newdir ~/data/{entity_type}/{state_code}/20240912/normal/L1/with_id/ -outdir ~/data/{entity_type}/{state_code}/20240912/normal/L3/ -stateAdditionalDataDir ~/data/{entity_type}/{state_code}/20240912/normal/L1/additional_info_json/ -seedBarAdditionalData ~/data/{entity_type}/{state_code}/20240912/normal/seed_bar_additional_data/{state_code}.json -seedSosAdditionalData ~/data/{entity_type}/{state_code}/20240912/normal/seed/sos_json/{state_code}.json -state {state_code} -entity A
```

### Python Scripts for Processing
```bash
cd ~/roshan/norm-input/ConfidenceScore

python3.7 findNeighbors1.py --file_path /home/teleport_user/data/{entity_type}/{state_code}/20240912/normal/L3/ 
python3.12 findPossibleScore2.py --file_path /home/teleport_user/data/{entity_type}/{state_code}/20240912/normal/L3/ 
python3.7 findPossibles3.py --file_path /home/teleport_user/data/{entity_type}/{state_code}/20240912/normal/L3/
```

### Validation Scripts
```bash
cd ~/roshan/norm-input/scripts/normalisation_input/ValidationScripts

python3.7 l3Validation.py --entity {entity_type} --state {state_code} --path /home/teleport_user/data/{entity_type}/{state_code}/20240912/normal --runID 20240912 --type normal --dryrun
cd
```

### AWS S3 Uploads
```bash
aws s3 cp --recursive ~/data/reports/{entity_type}/{state_code} s3://uc.analytics/staging/apollo/TEST/ALYA-739/{entity_type}/{state_code}/reports
aws s3 cp --recursive ~/data/{entity_type}/{state_code}/20240912/normal/L3 s3://uc.analytics/staging/apollo/TEST/ALYA-739/{entity_type}/{state_code}/L3
```

### Clean Up
```bash
cd data/
rm -rf {state_code}/
```

### Comments

#### Developer Testing Completion
The developer end testing is completed for the reports generated for attorney in `{state_code}`, and the L3 Files as well as reports have been uploaded to S3. The appropriate paths for the files are listed below:

- **Path to L3 folder:** `s3://uc.analytics/staging/apollo/TEST/ALYA-739/{entity_type}/{state_code}/L3/`
- **Missing seed entries in L3:** `s3://uc.analytics/staging/apollo/TEST/ALYA-739/{entity_type}/{state_code}/reports/{state_code}_{entity_type}_missingL3Seed.txt`
- **Missing L1 in L3:** `s3://uc.analytics/staging/apollo/TEST/ALYA-739/{entity_type}/{state_code}/reports/{state_code}_{entity_type}_missingL1inL3.txt`
- **Combined scenario reports:** `s3://uc.analytics/staging/apollo/TEST/ALYA-739/{entity_type}/{state_code}/reports/{state_code}_{entity_type}_l3_combinedScenario_reports.txt`

FYI: @Divya Raj K

#### Post-Testing Comments
@Madhav Bhat I have corrected the issues mentioned in the sheet and also uploaded the files. The paths for the files are listed below:

- **Path to L3 folder:** `s3://uc.analytics/staging/apollo/TEST/ALYA-739/{entity_type}/{state_code}/L3/`
- **Missing seed entries in L3:** `s3://uc.analytics/staging/apollo/TEST/ALYA-739/{entity_type}/{state_code}/reports/{state_code}_{entity_type}_missingL3Seed.txt`
- **Missing L1 in L3:** `s3://uc.analytics/staging/apollo/TEST/ALYA-739/{entity_type}/{state_code}/reports/{state_code}_{entity_type}_missingL1inL3.txt`
- **Combined scenario reports:** `s3://uc.analytics/staging/apollo/TEST/ALYA-739/{entity_type}/{state_code}/reports/{state_code}_{entity_type}_l3_combinedScenario_reports.txt`

FYI: @Divya Raj K

###Important Links:
- [Office Links](https://intranet.unicourt.net:9879/office-links)
- [AWS S3 UC Analytics Bucket](https://us-east-1.console.aws.amazon.com/s3/buckets/uc.analytics?region=us-east-1&bucketType=general&prefix=staging/apollo/TEST/ALYA-739/)
s
