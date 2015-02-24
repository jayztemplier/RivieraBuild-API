---
layout: index
---

## API Key
You can get an API key by signing in, then go to Settings. You'll see the API key, if not, click on "Generate new API key" to create a new one.


## Upload a build
    curl "http://beta.rivierabuild.com/api/upload"
    -F file=@"${TMP_FILE_PATH}"
    -F availability="${AVAILABILITY}"
    -F passcode="${PASSWORD}"
    -F app_id="${PASSWORD}"
    -F api_key="${API_KEY}"
    -F commit_sha="${COMMIT_SHA}"
    -F note="${NOTE}"
    -F version="${VERSION}"
    -F build_number="${BUILD_NUMBER}"

Result

    {"success":true,"file_url":"http://beta.rivierabuild.com/get/dovjek"}%

Params

* **file** *(string)*: path to the file to upload
* **availability** *(string)*: for how long the build will be available?  
* **passcode** *(string)*: Optional: password, if set, the password is required to download a build.
* **app_id** *(integer)*: Optional, recommended: ID of the application you want to put the build in. If not set, the build won't be assign to one of your applications.
* **api_key** *(string)*:  Optional, recommended: User API Key to link the build to your account. If not set, the build will be send as a guest user.
* **note** *(string)*: Optional: You can attach notes to your build!
* **commit_sha** *(string)*: Optional: last commit (sha) of the build. Can be useful to know what changes are included in the build
* **version** *(string)*: Optional: Version of the application (ex: 1.01)
* **build_number** *(string)*:  Optional: Build number (ex: 1.01b123)




### Availability Options

Once the availability time expires, the build is delete and not accessible anymore.

| Values  |
|---|
| 10_minutes  |
| 1_hour  |
| 3_hours  |
| 6_hours  |
| 12_hours  |
| 24_hours  |
| 1_week  |
| 2_weeks  |
| 1_month  |
| 2_months  |


## Get latest available build information
    curl "http://beta.rivierabuild.com/api/applications/:application_id/builds/latest"

Result

    {
      id: 59,
      build_name: "AnimalCrush.ipa",
      created_at: "2015-02-22T18:33:42.861Z",
      version: "1.0",
      build_number: "1.0",
      name: "Animal Crush",
      note: "Some note you wrote earlier",
      available_until: "2015-04-19T18:33:42.723Z",
      commit_sha: "ewfwefonwerfgoinrgerogrgojergpojergoeprgjerpogjer"
    }
