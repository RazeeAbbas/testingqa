name: Auto‑move project cards on pull request merge

on:
  pull_request:
    types: [closed]

jobs:
  move-card:
    if: ${{ github.event.pull_request.merged == true }}
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Move related issue to 'Done'
        uses: fojia/[email protected]
        with:
          project: 'YOUR_PROJECT_BOARD_NAME'
          column: 'Done'
          owner: 'YOUR_GITHUB_USERNAME_OR_ORG'
          repo: '${{ github.repository }}'
          github_token: ${{ secrets.GITHUB_TOKEN }}
