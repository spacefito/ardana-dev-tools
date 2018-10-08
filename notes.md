Add to ~/.bashrc (correct "ardanausername" to what you use

```
  export ARDANA_DEVELOPER=True
  export ARDANA_VAGRANT_VERSION=1.8.7
  export ARDANAUSER=ardanausername
  export ARDANA_SITE=provo
  eval "$(~/clm/ardana-dev-tools/bin/ardana-env)"
```

Install git:

```
   sudo zypper install git-core
```

Clone repos:
```
   mkdir clm
   cd clm
   git clone https://github.com/spacefito/ardana-dev-tools.git
   git clone https://github.com/spacefito/ardana-input-model.git
```

Set up runtime environment to assure correct ansible version is used:
```
   source ~/.bashrc
```
or 
```
   eval "$(~/clm/ardana-dev-tools/bin/ardana-env)"
```
