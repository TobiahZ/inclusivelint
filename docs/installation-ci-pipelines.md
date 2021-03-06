# Installation: CI Pipelines

### **GitHub Actions**

```yaml
jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2

    - name: Install inclusive linter
      run: |
        wget https://github.com/inclusivelint/inclusivelint/releases/download/<VERSION>/inclusivelint -O- | tr -d '\r' >inclusivelint
        sudo chmod +x inclusivelint && mv inclusivelint /usr/bin
        mkdir ~/.inclusivelint
        wget https://github.com/inclusivelint/inclusivelint/releases/download/<VERSION>/outputRelation.txt -O- | tr -d '\r' >outputRelation.txt
        sudo mv outputRelation.txt ~/.inclusivelint
    - name: Run inclusive linter
      run: |
        export TERM=xterm
        inclusivelint .
```

### **Azure DevOps**

```yaml
steps:
- script: |
    wget https://github.com/inclusivelint/inclusivelint/releases/download/<VERSION>/inclusivelint -O- | tr -d '\r' >inclusivelint
    sudo chmod +x inclusivelint && mv inclusivelint /usr/bin
    mkdir ~/.inclusivelint
    wget https://github.com/inclusivelint/inclusivelint/releases/download/<VERSION>/outputRelation.txt -O- | tr -d '\r' >outputRelation.txt
    sudo mv outputRelation.txt ~/.inclusivelint
  displayName: Install inclusive linter
- script: |
    export TERM=xterm
    inclusivelint .
  displayName: Run inclusive linter
```

## Next Steps

- [Adding new words to the dictionary](./add-new-words.md)
