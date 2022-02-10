<!-- start title -->

# GitHub Action:undefined

<!-- end title -->
<!-- start description -->

Builds an image, pushes to google artifact registry, and caches to gha as well as the `cache` tag. Specifically designed to work with google artifact registry. This is also designed to work on a release trigger by default, and will push latest, and the release tag

<!-- end description -->
<!-- start contents -->
<!-- end contents -->
<!-- start usage -->

```yaml
- uses: Unsupervisedcom/action-auth-build-push-image@undefined
  with:
    # gcloud service account credentials json
    credentials-json: ""

    # gcloud project id
    project-id: ""

    # artifact registry region
    # Default: us-central1
    region: ""

    # artifact registry repository
    # Default: images
    repository: ""

    # docker build secrets, comma separated string key=value
    # Default:
    secrets: ""

    # tag name, excluding tag version, such as `myapp`
    # Default: ${{ github.event.repository.name }}
    tag-name: ""

    # git tags to push, comma separated string such as `latest,v1.0.0`
    # Default: latest,${{ github.event.release.tag_name }}
    tag-versions: ""

    # git tag version to use for the registry cache
    # Default: cache
    cache-tag-version: ""
```

<!-- end usage -->
   <!-- start inputs -->

| **Input**               | **Description**                                                  |                  **Default**                  | **Required** |
| :---------------------- | :--------------------------------------------------------------- | :-------------------------------------------: | :----------: |
| **`credentials-json`**  | gcloud service account credentials json                          |                                               |   **true**   |
| **`project-id`**        | gcloud project id                                                |                                               |   **true**   |
| **`region`**            | artifact registry region                                         |                 `us-central1`                 |  **false**   |
| **`repository`**        | artifact registry repository                                     |                   `images`                    |  **false**   |
| **`secrets`**           | docker build secrets, comma separated string key=value           |                                               |  **false**   |
| **`tag-name`**          | tag name, excluding tag version, such as `myapp`                 |     `${{ github.event.repository.name }}`     |  **false**   |
| **`tag-versions`**      | git tags to push, comma separated string such as `latest,v1.0.0` | `latest,${{ github.event.release.tag_name }}` |  **false**   |
| **`cache-tag-version`** | git tag version to use for the registry cache                    |                    `cache`                    |  **false**   |

<!-- end inputs -->
   <!-- start outputs -->

| **Output**      | **Description** | **Default** | **Required** |
| :-------------- | :-------------- | ----------- | ------------ |
| `random-number` | Random number   |             |              |

<!-- end outputs -->
   <!-- start examples -->

### Example usage

```yaml
on: [push]

jobs:
  hello_world_job:
    runs-on: ubuntu-latest
    name: A job to say hello
    steps:
      - uses: actions/checkout@v2
      - id: foo
        uses: actions/hello-world-composite-action@v1
        with:
          who-to-greet: "Mona the Octocat"
      - run: echo random-number ${{ steps.foo.outputs.random-number }}
        shell: bash
```

<!-- end examples -->
<!-- start [.github/ghdocs/examples/] -->
<!-- end [.github/ghdocs/examples/] -->
