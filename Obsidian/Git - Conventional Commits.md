---
creation_time: 2024-07-25 17:53
parents:
  - "[[Git]]"
---

Мне хочется писать красивые, понятные, лаконичные коммиты. 
Аян говорил про conventional commits.

Можно писать коммиты через командную строку:
```sh
git commit -m "Add user authentication feature" -m "Implemented login and registration forms\n\nIntegrated with backend authentication API\n\nAdded unit tests for the authentication service\n\nUpdated documentation with usage examples"
```

Либо писать их в default text editor:
```sh
git commit
```

Можно настроить Default editor:
```sh
git config --global core.editor emacs
```

---
# Semantic Commit Messages
https://gist.github.com/joshbuchea/6f47e86d2510bce28f8e7f42ae84c716

See how a minor change to your commit message style can make you a better programmer.

Format: `<type>(<scope>): <subject>`

`<scope>` is optional

## Example

```
feat: add hat wobble
^--^  ^------------^
|     |
|     +-> Summary in present tense.
|
+-------> Type: chore, docs, feat, fix, refactor, style, or test.
```

More Examples:

- `feat`: (new feature for the user, not a new feature for build script)
- `fix`: (bug fix for the user, not a fix to a build script)
- `docs`: (changes to the documentation)
- `style`: (formatting, missing semi colons, etc; no production code change)
- `refactor`: (refactoring production code, eg. renaming a variable)
- `test`: (adding missing tests, refactoring tests; no production code change)
- `chore`: (updating grunt tasks etc; no production code change)

References:
- https://www.conventionalcommits.org/
- https://seesparkbox.com/foundry/semantic_commit_messages
- http://karma-runner.github.io/1.0/dev/git-commit-msg.html