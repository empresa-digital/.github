# Welcome to the TeamCollab Wiki!

TeamCollab is a small startup that values work life balance, high quality code
and tackling big problems when they are small and easy to manage.

In this page will cover some of the principles we use for coding and working together.

## Lean Software Development:

Lean Software Development is a set of ideas originally applied to car factories that converted
really well to the context of software development.

We recommend our members to learn those, a good short article on this topic is available here:

https://softdesign.com.br/blog/lean-development-sete-principios/#h-quais-sao-os-sete-principios-do-lean-software-development

- [x] Eliminar o desperdício (Eliminate waste)
- [x] Construir com qualidade (Build integrity in)
- [x] Amplificar o aprendizado (Amplify learning)
- [x] Adiar comprometimentos (Decide as late as possible)
- [x] Entregar rápido (Deliver as fast as possible)
- [x] Empoderar as pessoas (Empower the team)
- [x] Otimizar o todo (Optimize the whole)

## Code Style

We follow the Go Code Style with one small exception: [Initialisms](https://go.dev/wiki/CodeReviewComments#initialisms) being named with all caps is not enforced, but not frowned upon either. You should follow it in most cases just so it matches the most used style, but you should never add linter rules that enforce this as this prevents the creation of readable names for things like GRPCAPI, and also becomes a problem if you are implementing a mock for an external library that does not follow this convention. Linters should not give false positives.

## Linting

We rely heavily on code reviews for guaranteeing code style, so linters should concentrate in detecting errors and minimizing false positives. Each project should use a minimum set of linters that provide good coverage on common errors without creating exception cases where they might need to be ignored. Linters should never be ignored and, thus, linters that might require being ignored from time to time should never be added to our repos.

Linters that require cumbersome workarounds for not ignoring them should also be avoided, but are not prohibited.

## External Dependencies

Whenever you think about using an external dependency consider that there are
significant implied costs to every new dependency that add up over time:

1. Each member of your team will need to learn how to use every new dependency.
2. Members of other teams and future new members of the team will also have to learn about it.
3. If the dependency breaks or stops being maintained you get one of the most complicated types of problems
   where you need to debug internal details of an implementation you know little about and have no control over.

So think two or three times before deciding to use an external dependency.

If you decide that you need one give preference to libraries already used by the team.

And finally consider the option of writing the code you need yourself inside your current
project. More often than not what we actually need from an external dependency is small
enough that we can implement it in a couple hours as a local package.

### Rule of conduct about being blocked by external dependencies

This rule is compatible with what was mentioned above:

You should do everything in your power to prevent yourself and your co-workers from ever
getting blocked by problems on an external dependencies:

- Be careful with each new dependency you add as described on the previous section.
- Try to only use external packages that are battle-tested by time and big numbers of users.
- If you are in a situation where the external package is broken, consider copying it to
  a local package and fixing it there without waiting for third-parties.
- Finally, always allow yourself to drop external libraries in favor of other solutions,
  using a library should always be voluntary, never enforced by management.

If someone ever wants to centralize logic in the organization there are other ways of doing it
like creating a service mash or exposing an actual internal service behind an API, and these
should be the preferred methods of creating standards in the company.
