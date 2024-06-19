# Rover README

This is a fork of GitHub's recommended Copilot Metrics Viewer with Rover-specific configurations applied and added Codespaces support.

**You must have elevated GitHub permissions in order to run this reporter.**

Before getting started, this app requires the following scopes:

```
copilot,manage_billing:copilot,manage_billing:enterprise,read:enterprise,admin:org,codespace,repo
```

**1. Start the server**

If you are certain you have those scopes for the `roverdotcom` organization, you can start the app by running the startup script via terminal in a Codespace in this repo. This script will provision your GitHub token with the necessary scopes, set the token a the necessary environment variable, and start the web server.

```shell
./start-server.sh
```

**2. Forward and update Port Visibility**

Once the server starts, manually adjust port settings in VS Code:
1. Open the Ports panel (Cmd + Shift + P > Ports: Focus on Ports View)
2. Find the port the app is running on, and:
    1. Right-click > Change Port Protocol > HTTPS
    2. Right-click > Port Visibility > Private to Organization
3. View the running app by clicking the 🌐 globe icon next to the Forwarded Address in the Ports panel

Press Ctrl+C to stop the server.

If you have any issues, please reach out to the team in the #tech-development channel in Slack.

Original readme preserved below:

---

# GitHub Copilot Metrics Viewer
<p align="center">
  <img width="150" alt="image" src="https://github.com/github-copilot-resources/copilot-metrics-viewer/assets/3329307/8473a694-217e-4aa2-a3c7-2222a321c336">
</p>

This application displays a set of charts with various metrics related to GitHub Copilot for your <i>GitHub Organization</i> or <i>Enterprise Account</i>. These visualizations are designed to provide clear representations of the data, making it easy to understand and analyze the impact and adoption of GitHub Copilot. This app utilizes the [GitHub Copilot Metrics API](https://docs.github.com/en/enterprise-cloud@latest/rest/copilot/copilot-usage?apiVersion=2022-11-28).

## Video

https://github.com/github-copilot-resources/copilot-metrics-viewer/assets/3329307/bc7e2a16-cc73-43c4-887a-b50809c08533


## Charts

## Key Metrics
Here are the key metrics visualized in these charts:
1. **Acceptance Rate:** This metric represents the ratio of accepted lines to the total lines suggested by GitHub Copilot. This rate is an indicator of the relevance and usefulness of Copilot's suggestions.
<p align="center">
  <img width="800" alt="image" src="https://github.com/martedesco/copilot-metrics-viewer/assets/3329307/875a5f5f-5d8a-44bd-a4e9-0f663f2b2628">
</p>

3. **Total Suggestions** This chart illustrates the total number of code suggestions made by GitHub Copilot. It offers a view of the tool's activity and its engagement with users over time.

4. **Total Acceptances:** This visualization focuses on the total number of suggestions accepted by users.

<p align="center">
  <img width="800" alt="image" src="https://github.com/martedesco/copilot-metrics-viewer/assets/3329307/b84220ae-fbdc-4503-b50b-4689362bf364">
</p>

4. **Total Lines Suggested:** Showcases the total number of lines of code suggested by GitHub Copilot. This gives an idea of the volume of code generation and assistance provided.

5. **Total Lines Accepted:** As the name says, the total lines of code accepted by users (full acceptances) offering insights into how much of the suggested code is actually being utilized incorporated to the codebase.

<p align="center">
  <img width="800" alt="image" src="https://github.com/martedesco/copilot-metrics-viewer/assets/3329307/788c9b33-8e63-43a5-9ab9-98d8938dd9d9">
</p>

6. **Total Active Users:** Represents the number of active users engaging with GitHub Copilot. This helps in understanding the user base growth and adoption rate.

<p align="center">
  <img width="800" alt="image" src="https://github.com/martedesco/copilot-metrics-viewer/assets/3329307/bd92918f-3a11-492b-8490-877aaa768ca3">
</p>

## Languages Breakdown Analysis

Pie charts with the top 5 languages by accepted prompts and acceptance rate are displayed at the top.
<p align="center">
  <img width="800" alt="image" src="https://github.com/github-copilot-resources/copilot-metrics-viewer/assets/3329307/8ab0488a-89e6-486d-aa61-df3d178cd57c">
</p>

The language breakdown analysis tab also displays a table showing the Accepted Prompts, Accepted Lines of Code, and Acceptance Rate (%) for each language over the past 28 days. The entries are sorted by the number of _accepted lines of code descending_.

<p align="center">
  <img width="800" alt="image" src="https://github.com/github-copilot-resources/copilot-metrics-viewer/assets/3329307/38a4ff57-4974-4f60-a154-91db17b03678">
</p>

## Copilot Chat Metrics

<p align="center">
  <img width="800" alt="image" src="https://github.com/github-copilot-resources/copilot-metrics-viewer/assets/3329307/79867d5f-8933-4509-a58a-8c6deeb47536">
</p>

1. **Cumulative Number of Turns:** This metric represents the total number of turns (interactions) with the Copilot over the past 28 days. A 'turn' includes both user inputs and Copilot's responses.

2. **Cumulative Number of Acceptances:** This metric shows the total number of lines of code suggested by Copilot that have been accepted by users over the past 28 days.

3. **Total Turns | Total Acceptances Count:** This is a chart that displays the total number of turns and acceptances

4. **Total Active Copilot Chat Users:** a bar chart that illustrates the total number of users who have actively interacted with Copilot over the past 28 days.

## Seat Analysis

![image](https://github.com/DevOps-zhuang/copilot-metrics-viewer/assets/54096296/d1fa9d1d-4fab-4e87-84ba-7be189dd4dd0)

1. **Total Assigned:** This metric represents the total number of Copilot seats assigned within current organization.

2. **Assigned But Never Used:** This metric shows seats that were assigned but never within the current organization. The assigned timestamp is also displayed in the below chart.

3. **No Activity in the Last 7 days:** never used seats or seats used, but with no activity in the past 7 days.

4. **No Activity in the last 7 days (including never used seats):** a table to display seats that have had no activity in the past 7 days, ordered by the date of last activity. Seats that were used earlier are displayed at the top.



## Setup instructions

In the `.env` file, you can configure several environment variables that control the behavior of the application.

#### VUE_APP_SCOPE

The `VUE_APP_SCOPE` environment variable in the `.env` file determines the scope of the API calls made by the application. It can be set to either 'enterprise' or 'organization'.

- If set to 'enterprise', the application will target API calls to the GitHub Enterprise account defined in the `VUE_APP_GITHUB_ENT` variable.
- If set to 'organization', the application will target API calls to the GitHub Organization account defined in the `VUE_APP_GITHUB_ORG` variable.

For example, if you want to target the API calls to an organization, you would set `VUE_APP_SCOPE=organization` in the `.env` file.

````
VUE_APP_SCOPE=organization

VUE_APP_GITHUB_ORG= <YOUR-ORGANIZATION>

VUE_APP_GITHUB_ENT=
````


#### VUE_APP_MOCKED_DATA

To access Copilot metrics from the last 28 days via the API and display actual data, set the following boolean environment variable to `false`:

```
  VUE_APP_MOCKED_DATA=false
```

#### VUE_APP_GITHUB_TOKEN
Specifies the GitHub Personal Access Token utilized for API requests. Generate this token with the following scopes: _copilot_, _manage_billing:copilot_, _manage_billing:enterprise_, _read:enterprise_, _admin:org_.

```
  VUE_APP_GITHUB_TOKEN=
```

## Install dependencies
```
npm install
```

### Compiles and runs the application
```
npm run serve
```

### Docker build
```
docker build -t copilot-metrics-viewer .
```

### Docker run
```
docker run -p 8080:80 copilot-metrics-viewer
```
The application will be accessible at http://localhost:8080

## License

This project is licensed under the terms of the MIT open source license. Please refer to [MIT](./LICENSE.txt) for the full terms.

## Maintainers

[@martedesco](https://github.com/martedesco)

## Support

This project is independently developed and maintained, and is not an official GitHub product. It thrives through the dedicated efforts of myself ([@martedesco](https://github.com/martedesco)) and our wonderful contributors. A heartfelt thanks to all our contributors! ✨

I aim to provide support through [GitHub Issues](https://github.com/github-copilot-resources/copilot-metrics-viewer/issues). While I strive to stay responsive, I can't guarantee immediate responses. For critical issues, please include "CRITICAL" in the title for quicker attention. 🙏🏼

### Coming next 🔮
- Team slicing
- Persistence layer
