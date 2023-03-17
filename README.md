# CIS TailoredProfile for ARO

Azure Red Hat OpenShift is a 1st party Azure managed service.  It is jointly engineered and supported by Microsoft and Red Hat.

As a managed service, there are certain aspects of an ARO cluster that you are not allowed to change.  Perhaps most importantly, kubelet config.

The `TailoredProfile`s in this repository reflect this by removing any controls from the default `cis` scans that would put your ARO cluster out of support.

This is a work in progress.  Currently, this removed any kubelet-related checks from the `ocp4-cis` scan.

To use this profile:

First, create the `TailoredProfile:

```
oc apply -f ocp4-cis-tailoredprofile.yaml -n openshift-compliance
```

Next, create a `ScanSettingBinding` that references the profile:

```
oc apply -f scansettingbinding.yaml -n openshift-compliance
```

Then... wait for the scan to complete.