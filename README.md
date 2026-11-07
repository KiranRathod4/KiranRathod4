<!-- Sheet 1 of 2: identity. The stamp lands about two seconds after load. -->
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="./assets/header-dark.svg" />
  <source media="(prefers-color-scheme: light)" srcset="./assets/header-light.svg" />
  <img alt="Engineering drawing of Kiran Rathod, SDET and DevOps engineer. Code. Cloud. Quality. Repeat. A test harness asserts against web, api and db pods in a Kubernetes cluster built with Terraform on AWS. Title block status: PASSED." src="./assets/header-dark.svg" width="100%" />
</picture>

<p align="center">
  <img src="https://komarev.com/ghpvc/?username=KiranRathod4&label=Profile%20views&color=0A2A4F&style=flat-square" alt="Profile views" />
  <img src="https://img.shields.io/badge/Open_to-SDET_%26_DevOps_roles-FFB23F?style=flat-square&labelColor=0A2A4F" alt="Open to SDET and DevOps roles" />
  <img src="https://img.shields.io/badge/Flaky_tests-0-5BE49B?style=flat-square&labelColor=0A2A4F" alt="Flaky tests: 0" />
  <img src="https://img.shields.io/badge/Friday_deploys-skipped-8FB0D3?style=flat-square&labelColor=0A2A4F" alt="Friday deploys: skipped" />
</p>

I'm an SDET who also owns the pipeline. I design test cases, automate them with Playwright, PyTest and REST Assured, wire them into CI, and build the Docker, Kubernetes and Terraform infrastructure they run against. The goal is simple: a release should be something the pipeline proves, not something a person hopes.

I break things in staging so they don't break in production.

<br/>

## About me, as a manifest

```yaml
apiVersion: people/v1
kind: Engineer
metadata:
  name: kiran-rathod
  labels:
    role: sdet
    also: devops
    location: bengaluru-in
spec:
  education:
    degree: B.Tech, Computer Science & Business Systems
    university: VTU
    graduation: 2026
  quality:
    automation: [Selenium, PyTest, TestNG]
    api: [REST Assured, Postman, Swagger, cURL]
    manual: [test case design, exploratory testing, defect tracking in Jira]
    data: [SQL]
  delivery:
    ci: GitHub Actions
    containers: [Docker, Kubernetes, Helm]
    infrastructure: Terraform on AWS
    security: [SonarQube, Trivy]
    observability: [Prometheus, Grafana]
  readinessProbe:
    exec: ["pytest", "-q"]        # not ready until the suite is green
  resources:
    limits:
      flakyTests: 0
```

<br/>

## My test suite

```diff
$ pytest tests/test_kiran.py -v

+ test_kiran.py::test_designs_test_cases_before_scripts            PASSED   [ 12%]
+ test_kiran.py::test_automates_ui_flows_with_selenium             PASSED   [ 25%]
+ test_kiran.py::test_validates_api_contracts_with_rest_assured    PASSED   [ 37%]
+ test_kiran.py::test_quality_gate_blocks_bad_merges               PASSED   [ 50%]
+ test_kiran.py::test_images_are_scanned_before_deploy             PASSED   [ 62%]
+ test_kiran.py::test_infrastructure_is_reproducible               PASSED   [ 75%]
+ test_kiran.py::test_zero_tolerance_for_flaky_tests               PASSED   [ 87%]
- test_kiran.py::test_deploy_on_friday_evening                     SKIPPED (no Friday-evening deploys) [100%]

+ ===================== 7 passed, 1 skipped in 0.42s =====================
```

<details>
<summary><b>View the test source</b></summary>
<br/>

```python
import pytest
from people import Kiran


@pytest.fixture
def kiran():
    return Kiran(role="SDET", also="DevOps", city="Bengaluru")


def test_designs_test_cases_before_scripts(kiran):
    plan = kiran.plan("checkout flow")
    assert plan.test_cases and not plan.scripts   # design first, automate second


def test_automates_ui_flows_with_selenium(kiran):
    assert "Selenium" in kiran.automation


def test_validates_api_contracts_with_rest_assured(kiran):
    assert kiran.api_tests.cover("status", "schema", "auth", "edge cases")


def test_quality_gate_blocks_bad_merges(kiran):
    assert kiran.pipeline.gate("SonarQube").blocks_on_failure


def test_images_are_scanned_before_deploy(kiran):
    assert kiran.pipeline.step("trivy").runs_before("deploy")


def test_infrastructure_is_reproducible(kiran):
    assert kiran.terraform.plan() == kiran.terraform.plan()   # same input, same infra


def test_zero_tolerance_for_flaky_tests(kiran):
    assert kiran.flaky_tests == 0


@pytest.mark.skip(reason="no Friday-evening deploys")
def test_deploy_on_friday_evening(kiran):
    kiran.deploy(env="prod", day="Friday", time="18:30")
```

</details>

<br/>

## How I ship

Every change goes through the same eight stations. Tests run before anything is built, images are scanned before anything is deployed, and whatever production tells me goes back into the backlog.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="./assets/pipeline-dark.svg" />
  <source media="(prefers-color-scheme: light)" srcset="./assets/pipeline-light.svg" />
  <img alt="Delivery pipeline: 1 commit (git, GitHub Actions), 2 quality gate (SonarQube), 3 unit tests (PyTest, TestNG), 4 API tests (REST Assured, Postman), 5 UI tests (Selenium plus exploratory), 6 build and scan (Docker, Trivy), 7 deploy (Terraform, Helm, Kubernetes on AWS), 8 observe (Prometheus, Grafana). Defects and alerts loop back to the backlog in Jira." src="./assets/pipeline-dark.svg" width="100%" />
</picture>

<br/>

## Toolchain

<table>
  <tr>
    <td width="50%" valign="top">
      <h3>Quality engineering</h3>
      <p>
        <b>UI automation</b><br/>
        <img src="https://img.shields.io/badge/Selenium-0A2A4F?style=flat-square&logo=selenium&logoColor=43B02A" alt="Selenium" />
        <img src="https://img.shields.io/badge/PyTest-0A2A4F?style=flat-square&logo=pytest&logoColor=0A9EDC" alt="PyTest" />
        <img src="https://img.shields.io/badge/TestNG-0A2A4F?style=flat-square" alt="TestNG" />
      </p>
      <p>
        <b>API testing</b><br/>
        <img src="https://img.shields.io/badge/REST_Assured-0A2A4F?style=flat-square&logo=openjdk&logoColor=white" alt="REST Assured" />
        <img src="https://img.shields.io/badge/Postman-0A2A4F?style=flat-square&logo=postman&logoColor=FF6C37" alt="Postman" />
        <img src="https://img.shields.io/badge/Swagger-0A2A4F?style=flat-square&logo=swagger&logoColor=85EA2D" alt="Swagger" />
        <img src="https://img.shields.io/badge/cURL-0A2A4F?style=flat-square&logo=curl&logoColor=white" alt="cURL" />
        <img src="https://img.shields.io/badge/JSON-0A2A4F?style=flat-square&logo=json&logoColor=white" alt="JSON" />
      </p>
      <p>
        <b>Manual testing and tracking</b><br/>
        <img src="https://img.shields.io/badge/Test_case_design-0A2A4F?style=flat-square" alt="Test case design" />
        <img src="https://img.shields.io/badge/Exploratory_testing-0A2A4F?style=flat-square" alt="Exploratory testing" />
        <img src="https://img.shields.io/badge/Jira-0A2A4F?style=flat-square&logo=jira&logoColor=2684FF" alt="Jira" />
        <img src="https://img.shields.io/badge/SQL-0A2A4F?style=flat-square&logo=mysql&logoColor=4479A1" alt="SQL" />
      </p>
    </td>
    <td width="50%" valign="top">
      <h3>Delivery engineering</h3>
      <p>
        <b>CI/CD and containers</b><br/>
        <img src="https://img.shields.io/badge/GitHub_Actions-0A2A4F?style=flat-square&logo=githubactions&logoColor=2088FF" alt="GitHub Actions" />
        <img src="https://img.shields.io/badge/Git-0A2A4F?style=flat-square&logo=git&logoColor=F05032" alt="Git" />
        <img src="https://img.shields.io/badge/Docker-0A2A4F?style=flat-square&logo=docker&logoColor=2496ED" alt="Docker" />
        <img src="https://img.shields.io/badge/Kubernetes-0A2A4F?style=flat-square&logo=kubernetes&logoColor=326CE5" alt="Kubernetes" />
        <img src="https://img.shields.io/badge/Helm-0A2A4F?style=flat-square&logo=helm&logoColor=white" alt="Helm" />
      </p>
      <p>
        <b>Cloud and infrastructure as code</b><br/>
        <img src="https://img.shields.io/badge/AWS-0A2A4F?style=flat-square&logo=amazonwebservices&logoColor=FF9900" alt="AWS" />
        <img src="https://img.shields.io/badge/Terraform-0A2A4F?style=flat-square&logo=terraform&logoColor=7B42BC" alt="Terraform" />
        <img src="https://img.shields.io/badge/Linux-0A2A4F?style=flat-square&logo=linux&logoColor=FCC624" alt="Linux" />
        <img src="https://img.shields.io/badge/Python-0A2A4F?style=flat-square&logo=python&logoColor=FFD43B" alt="Python" />
      </p>
      <p>
        <b>Security and observability</b><br/>
        <img src="https://img.shields.io/badge/SonarQube-0A2A4F?style=flat-square&logo=sonarqube&logoColor=4E9BCD" alt="SonarQube" />
        <img src="https://img.shields.io/badge/Trivy-0A2A4F?style=flat-square&logo=trivy&logoColor=1904DA" alt="Trivy" />
        <img src="https://img.shields.io/badge/Prometheus-0A2A4F?style=flat-square&logo=prometheus&logoColor=E6522C" alt="Prometheus" />
        <img src="https://img.shields.io/badge/Grafana-0A2A4F?style=flat-square&logo=grafana&logoColor=F46800" alt="Grafana" />
      </p>
    </td>
  </tr>
</table>

<details>
<summary><b>Also in the toolbox: MLOps and data</b></summary>
<br/>
<p>
  <img src="https://img.shields.io/badge/MLflow-0A2A4F?style=flat-square&logo=mlflow&logoColor=0194E2" alt="MLflow" />
  <img src="https://img.shields.io/badge/DVC-0A2A4F?style=flat-square&logo=dvc&logoColor=945DD6" alt="DVC" />
  <img src="https://img.shields.io/badge/Hugging_Face-0A2A4F?style=flat-square&logo=huggingface&logoColor=FFD21E" alt="Hugging Face" />
  <img src="https://img.shields.io/badge/LangChain-0A2A4F?style=flat-square&logo=langchain&logoColor=white" alt="LangChain" />
  <img src="https://img.shields.io/badge/Streamlit-0A2A4F?style=flat-square&logo=streamlit&logoColor=FF4B4B" alt="Streamlit" />
  <img src="https://img.shields.io/badge/TensorFlow-0A2A4F?style=flat-square&logo=tensorflow&logoColor=FF6F00" alt="TensorFlow" />
  <img src="https://img.shields.io/badge/PyTorch-0A2A4F?style=flat-square&logo=pytorch&logoColor=EE4C2C" alt="PyTorch" />
  <img src="https://img.shields.io/badge/scikit--learn-0A2A4F?style=flat-square&logo=scikitlearn&logoColor=F7931E" alt="scikit-learn" />
  <img src="https://img.shields.io/badge/Pandas-0A2A4F?style=flat-square&logo=pandas&logoColor=white" alt="Pandas" />
  <img src="https://img.shields.io/badge/NumPy-0A2A4F?style=flat-square&logo=numpy&logoColor=4DABCF" alt="NumPy" />
  <img src="https://img.shields.io/badge/Power_BI-0A2A4F?style=flat-square&logo=powerbi&logoColor=F2C811" alt="Power BI" />
</p>
</details>

<!--
## Featured work
Pin cards for your best SDET / DevOps repos. Replace REPO_NAME, then delete these comment markers.

<p>
  <a href="https://github.com/KiranRathod4/REPO_NAME">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats.vercel.app/api/pin/?username=KiranRathod4&repo=REPO_NAME&bg_color=0A2A4F&title_color=FFB23F&text_color=E6EEF7&icon_color=5BE49B&border_color=1D4E89" />
      <img src="https://github-readme-stats.vercel.app/api/pin/?username=KiranRathod4&repo=REPO_NAME&bg_color=F3F7FC&title_color=B86E00&text_color=0A2A4F&icon_color=13874B&border_color=C9D8EA" alt="REPO_NAME" />
    </picture>
  </a>
</p>
-->

<br/>

## Activity

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats.vercel.app/api?username=KiranRathod4&show_icons=true&hide_title=true&include_all_commits=true&bg_color=0A2A4F&text_color=E6EEF7&icon_color=5BE49B&title_color=FFB23F&border_color=1D4E89" />
    <img height="165" src="https://github-readme-stats.vercel.app/api?username=KiranRathod4&show_icons=true&hide_title=true&include_all_commits=true&bg_color=F3F7FC&text_color=0A2A4F&icon_color=13874B&title_color=B86E00&border_color=C9D8EA" alt="GitHub stats" />
  </picture>
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://streak-stats.demolab.com?user=KiranRathod4&background=0A2A4F&border=1D4E89&stroke=1D4E89&ring=FFB23F&fire=FFB23F&currStreakNum=E6EEF7&sideNums=E6EEF7&currStreakLabel=FFB23F&sideLabels=8FB0D3&dates=8FB0D3" />
    <img height="165" src="https://streak-stats.demolab.com?user=KiranRathod4&background=F3F7FC&border=C9D8EA&stroke=C9D8EA&ring=B86E00&fire=B86E00&currStreakNum=0A2A4F&sideNums=0A2A4F&currStreakLabel=B86E00&sideLabels=4D6B8C&dates=4D6B8C" alt="Contribution streak" />
  </picture>
</p>

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/KiranRathod4/KiranRathod4/output/github-snake-dark.svg" />
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/KiranRathod4/KiranRathod4/output/github-snake.svg" />
  <img alt="A snake eating my contribution graph" src="https://raw.githubusercontent.com/KiranRathod4/KiranRathod4/output/github-snake.svg" />
</picture>

<br/>

## Get in touch

Hiring for QA automation, SDET or DevOps work, or want a second pair of eyes on a flaky suite? Reach out.

<p>
  <a href="mailto:kiranrathod4299@gmail.com"><img src="https://img.shields.io/badge/Email-0A2A4F?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /></a>
  <a href="https://www.linkedin.com/in/kiranrathod05/"><img src="https://img.shields.io/badge/LinkedIn-0A2A4F?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
  <a href="https://github.com/KiranRathod4"><img src="https://img.shields.io/badge/GitHub-0A2A4F?style=for-the-badge&logo=github&logoColor=white" alt="GitHub" /></a>
  <a href="https://www.instagram.com/kiran_nnnn05/"><img src="https://img.shields.io/badge/Instagram-0A2A4F?style=for-the-badge&logo=instagram&logoColor=white" alt="Instagram" /></a>
  <a href="https://buymeacoffee.com/kiranrathod"><img src="https://img.shields.io/badge/Buy_me_a_coffee-FFB23F?style=for-the-badge&logo=buymeacoffee&logoColor=0A2A4F" alt="Buy me a coffee" /></a>
</p>
