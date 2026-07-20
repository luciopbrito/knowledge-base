# Info

## Table of contents

- [how-to content](how-to.md)
- [architecture content](architecture.md)
 
## About Semantic Versioning

Semantic Versioning, often referred to as "SemVer," is a formal specification for how version numbers are assigned and incremented. It uses a three-part numbering system: **MAJOR.MINOR.PATCH**. This system helps developers and users understand the nature of changes between versions.

Here's what each part signifies:

* **MAJOR (X.y.z):** Incremented when you make incompatible API changes. This means code written for a previous major version might not work with the new one without modifications.
* **MINOR (x.Y.z):** Incremented when you add new functionality in a backward-compatible manner. Existing code should still work with the new minor version.
* **PATCH (x.y.Z):** Incremented when you make backward-compatible bug fixes. These changes should not break existing functionality.

Additionally, pre-release and build metadata can be appended to the version number using hyphens and plus signs, respectively (e.g., 1.0.0-alpha+001).

**Real-World Examples for a Frontend App:**

Imagine you're developing a React component library used across multiple frontend applications in your organization.

* **Initial Release:** `1.0.0`
  * This is your first stable release.

* **Patch Release (Bug Fix):** `1.0.1`
  * You found a small bug in a button component's styling (e.g., `Button.js` had a CSS issue on hover).
  * Fixing this bug doesn't change any of the component's props or how it's used.
  * *Example commit message:* `fix: Corrected hover state for primary button`

* **Minor Release (New Feature, Backward Compatible):** `1.1.0`
  * You add a new `loading` prop to your `Button` component that shows a spinner while the button is disabled. Existing uses of the `Button` component still work as before, but now developers can optionally use the new prop.
  * You also introduce a new `Avatar` component that was not present before.
  * *Example commit message:* `feat: Add loading state to Button component; feat: Introduce new Avatar component`

* **Major Release (Breaking Change):** `2.0.0`
  * You decide to refactor your `Input` component. Previously, it took a `value` prop as a string, but now you want it to accept an `onChange` prop that returns an event object, aligning with standard HTML input behavior, which is a breaking API change for existing implementations.
  * You also decide to remove the `DatePicker` component entirely due to low usage and high maintenance.
  * *Example commit message:* `BREAKING CHANGE: Input component now uses standard onChange event handler; refactor: Remove deprecated DatePicker component`

By following SemVer, other teams consuming your component library can easily understand the impact of upgrading to a new version. A patch update (`1.0.1` to `1.0.2`) is generally safe, a minor update (`1.0.0` to `1.1.0`) brings new features but should still be compatible, and a major update (`1.0.0` to `2.0.0`) signals that they need to review the changelog and potentially update their code.

> source: <https://semver.org/>

## About Conventional Commits

| Type | Meaning | Example |
| ---- | ------- | ------- |
| `test` | indica qualquer tipo de criação ou alteração de códigos de teste.| Exemplo: Criação de testes unitários. |
| `feat` | indica o desenvolvimento de uma nova feature ao projeto.| Exemplo: Acréscimo de um serviço, funcionalidade, endpoint, etc. |
| `refactor` | usado quando houver uma refatoração de código que não tenha qualquer tipo de impacto na lógica/regras de negócio do sistema.| Exemplo: Mudanças de código após um code review |
| `style` | empregado quando há mudanças de formatação e estilo do código que não alteram o sistema de nenhuma forma.| Exemplo: Mudar o style-guide, mudar de convenção lint, arrumar indentações, remover espaços em brancos, remover comentários, etc..|
| `fix` | utilizado quando há correção de erros que estão gerando bugs no sistema.| Exemplo: Aplicar tratativa para uma função que não está tendo o comportamento esperado e retornando erro.|
| `chore` | indica mudanças no projeto que não afetem o sistema ou arquivos de testes. São mudanças de desenvolvimento.| Exemplo: Mudar regras do eslint, adicionar prettier, adicionar mais extensões de arquivos ao .gitignore |
| `docs` | usado quando há mudanças na documentação do projeto.| Exemplo: adicionar informações na documentação da API, mudar o README, etc. |
| `build` | utilizada para indicar mudanças que afetam o processo de build do projeto ou dependências externas.| Exemplo: Gulp, adicionar/remover dependências do npm, etc.|
| `perf` | indica uma alteração que melhorou a performance do sistema.| Exemplo: alterar ForEach por while, melhorar a query ao banco, etc.|
| `ci` | utilizada para mudanças nos arquivos de configuração de CI.| Exemplo: Circle, Travis, BrowserStack, etc.|
| `revert` | indica a reverão de um commit anterior.|  |

## About How to Measure Task Priority

| Priority | Description | Example |
| ---------| ------------| --------|
| P0       | Must be addressed immediately. Blocking issues (e.g., broken builds, major regressions). | Build fails on main branch, security vulnerabilities. |
| P1       | High priority. Should be addressed before the next release. Important bug fixes or improvements.| Performance bottleneck, feature not working as expected.|
| P2       | Medium priority. Should be addressed, but not urgent. | Minor bugs, cleanup tasks, non-blocking enhancements. |
| P3       | Low priority. Nice to have. Could be addressed if time permits. | Code refactoring, minor UX improvements. |
| P4       | Lowest priority. May never be addressed unless someone is particularly motivated.| Cosmetic issues, very edge-case feature requests. |

source: <https://beam.apache.org/contribute/issue-priorities/>

## About How to Measure Task Size

| Size | Meaning | Example |
| ---- | ------- | ------- |
| XS   | Trivial, almost no effort | Typo fix, small config change |
| S    | Small task, quick fix | Update UI text, minor style change |
| M    | Medium complexity | Add form validation, new API endpoint |
| L    | Complex, multiple steps | New feature with backend/frontend |
| XL   | Very complex, many unknowns | Major refactor, large module |

| Size | Ideal Days (Optional) |
| ---- | --------------------- |
| XS | < 0.5 day |
| S | 0.5 – 1 day |
| M | 1 – 3 days |
| L | 3 – 5 days |
| XL | 5+ days |
