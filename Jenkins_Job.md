# JENKINS JOBS AND SETTINGS (FAST FORWARD)

## Job Sequence
###  1. addressbookcompile
###  2. addressbookcodereview
###  3. addressbookbuild
###  4. addressbookunittest
###  5. addressbookmetrictest
###  6. addressbookpackage
###  7. addressbookTonCatInstall          (Ansible Master/Slave) (PROD, UAT, QA )
###  8. addressbookDeployWar              (Ansible) (PROD, UAT, QA )
###  9. addressbookBuildImage             (Docker)
###  10. addressbookPushImage             (Docker)
###  11. addressbookDeployContainer       (Docker)
