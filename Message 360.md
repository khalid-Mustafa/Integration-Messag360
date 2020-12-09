# Message 360

[![N|](https://i.ibb.co/zPNCNXG/slogan.jpg)]()


# Implemenattion Guide

  - steps are mentioned below:


### Tech

You can following methods from both fragment and activity

### How to Check Message 360 is Installed



```sh
  private boolean isAppInstalled(Context context, String packageName) {
        PackageManager pm = context.getPackageManager();
        try {
            pm.getPackageInfo(packageName, PackageManager.GET_ACTIVITIES);
            return true;
        } catch (PackageManager.NameNotFoundException ignored) {

        }
        return false;
    }
```

### How to Check Message 360 is Enabled

```sh
 private boolean isAppEnabled(Context context, String packageName) {
        boolean appStatus = false;
        try {
            ApplicationInfo ai = context.getPackageManager().getApplicationInfo(packageName, 0);
            if (ai != null) {
                appStatus = ai.enabled;
            }
        } catch (PackageManager.NameNotFoundException e) {
            e.printStackTrace();
        }
        return appStatus;
    }
```

### How to Open Message 360 App (Installed on Device)

```sh
    String applicationId = "com.app.message360";
    Intent intent = getPackageManager().getLaunchIntentForPackage(applicationId);
    intent.putExtra("PARAM_NUMBER","03472462508");
    tartActivity(intent);

```
### How to Open Playstore for  Message 360 App (If Not Installed)

```sh
  Intent intent = new Intent(Intent.ACTION_VIEW).setData(Uri.parse("https://play.google.com/store/apps/details?id=" + applicationId));
  startActivity(intent);
  
  ```
  ### Full Example

```sh
if (isAppInstalled(this, applicationId)) {
            if (isAppEnabled(this, applicationId)) {
               Intent intent = getPackageManager().getLaunchIntentForPackage(applicationId);
               intent.putExtra("PARAM_NUMBER","03472462508");
               startActivity(intent);

            }else {
                Toast.makeText(this, "Application is Disabled", Toast.LENGTH_SHORT).show();
            }
        } else {
            Intent intent = new Intent(Intent.ACTION_VIEW).setData(Uri.parse("https://play.google.com/store/apps/details?id=" + applicationId));
            startActivity(intent);
        }
...


