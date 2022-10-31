# GCLOUD Cheat-sheet

* Get current project 
    ```
    gcloud config get-value project    
    ```

* Set current project 
    ```
    gcloud config set project project-id    
    ```

* Deploy cloud function
    ```
    gcloud beta functions deploy myFunction --source=. --runtime nodejs16 --region europe-west1 --trigger-http --docker-repository=projects/MY_PROJECT/locations/europe-west1/repositories/MY_REPO 
    ```
    - https://cloud.google.com/functions/docs/building#image_registry_options    
