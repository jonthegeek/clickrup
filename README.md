# clickrup <img src="https://raw.githubusercontent.com/psolymos/clickrup/master/inst/images/clickrup.jpg" align="right" style="padding-left:10px;background-color:white;" width="200px" />
> Interacting with the ClickUp v2 API from R

[ClickUp](https://clickup.com/?noRedirect=true) is a cloud-based collaboration and project management tool. 
Features include tasks, docs, chat, goals, and [more](https://clickup.com/features).

The {clickrup} R package wraps the ClickUp [API v2](https://clickup.com/api). 
See the [roadmap](https://github.com/psolymos/clickrup/issues/1) for what is currently included in the package.

## Prerequisites

Install the {clickrup} package:

```R
remotes::install_github("psolymos/clickrup")
```

### Set up personal access token (PAT)

Follow this [tutorial](https://docs.clickup.com/en/articles/1367130-getting-started-with-the-clickup-api):

- Sign up for ClickUp (you can use this referral [link](https://clickup.com?fp_ref=peter51) to do so, it's free)
- Navigate to your personal *Settings* 
- Click *Apps* in the left sidebar
- Click *Generate* to create your API token
- Click *Copy* to copy the key to your clipboard 

Add your ClickUp token as an environment variable. There are 
[various ways](https://stackoverflow.com/questions/12291418/how-can-i-make-r-read-my-environmental-variables) of doing that. 
The simplest is to use `Sys.setenv(CU_PAT="your_token")` adding your token from the previous step.

## API endpoints

The first step you want to do is to get the IDs for your workspaces (teams is the legacy term for this in the API):

```R
library(clickrup)

cu_get_teams()
```

If your setup was successful, `cu_get_teams()` should return a list with the workspace IDs and names.

The easiest way to get going with the various endpoints is to browse the [API v2 documentation](https://clickup.com/api).
Once you found what you are after, just look at the API heading. There is **Get Teams**, the R function
is prepended with `cu_` (to facilitate RStudio suggestions), then comes the heading in lower case and spaces replaced by underscores.
For example **Get Filtered Team Tasks** will be `cu_get_filtered_team_tasks()`.

Function arguments are the *Parameters* listed on the API page, `...` passes optional parameters, query parameters, 
or elements for the body.

## Issues

https://github.com/psolymos/clickrup/issues

## License

[MIT](LICENSE) &copy; 2020 Peter Solymos
