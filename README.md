Run using: tsc --module commonjs --jsx preserve app.tsx

This is intended to show that without isolating referenced globals even for proper external modules
you will run into issues. This project has the following structure:

- app
  - react
  - someComponent
    - react

Note that react and someComponent are proper external modules. react introduces a global in the `JSX`
namespace which is required for proper JSX integration. someComponent also references a react
definition so that it can access React.Component. In this case, the JSX namespace results in a
"Duplicate identifier" error.