cache:
  paths:
    - .\build

stages:          # List of stages for jobs, and their order of execution
  - build
  - test

build-job:       # This job runs in the build stage, which runs first.
  stage: build
  tags:
    - netology
  script:
    - echo "Building"
    - mkdir build
    - echo "this is test" > .\build\info.txt

test-job:   # This job runs in the test stage.
  stage: test    # It only starts when the job in the build stage completes successfully.
  tags:
    - netology
  script:
    - echo "Testing"
    - dir .\build\info.txt
