# MoonMail Tips
When using [MoonMail](https://github.com/microapps/MoonMail), the documentation had some gaps. Below are some tips to help get to the next step.

## serverless
MoonMail is deployed using the 0.x verison of serverless. This means if you have the 1.x version installed, you'll need to uninstall it and install the 0.x version. For instance:
```
npm uninstall -g serverless
npm install -g serverless@0.5.6
```

## python
MoonMail uses node-gyp, which only runs in Python 2.7. If you have 3.5 installed and first on the path, then it won't work.
