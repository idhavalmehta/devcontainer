```
RUN curl -fsSL https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.4/install.sh | bash
```

This does the following:
- downloads nvm install script
- runs the contents of the install script in bash
- appends the necessary exports in ~/.bashrc because we run the script in a bash shell
- downloads and install node version specified by NODE_VERSION environment variable using nvm
- sets the default nvm node alias to the installed version

This is why we do not have to follow all the steps mentioned in the nvm install step in their GitHub repo.
