# Set text output v1

A simple composite actions to set the job output while maintaining the text format e.g. markdown format and multi-line strings.

[![test](https://github.com/mkungla/actions-set-text-output/actions/workflows/test.yml/badge.svg)](https://github.com/mkungla/actions-set-text-output/actions/workflows/test.yml)

# Usage

**NOTE:** `mkungla/actions-set-text-output@v1` is branch which always has latest `v1.x.x` version.  

```yml
- uses: mkungla/actions-set-text-output@v1
  id: content
  with:
    text: |
      # Set text output

      A simple composite actions to set the job output while maintaining the text format e.g. markdown format.
```

# Example

```yml
  usage:
    runs-on: ubuntu-latest
    outputs:
      content: ${{ steps.content.outputs.value }}
    steps:
      - uses: mkungla/actions-set-text-output@v1
        id: content
        with:
          text: |
            # Set text output

            A simple composite actions to set the job output while maintaining the text format e.g. markdown format.
  result:
    runs-on: ubuntu-latest
    needs: usage
    steps:
      - if: ${{ !startsWith(needs.test-usage.outputs.content, '# Set text output') }}
        run: exit 1
      - run: echo "${{ needs.usage.outputs.content }}" 
```
