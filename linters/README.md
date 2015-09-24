## `.eslintrc`

Our `.eslintrc` requires the following NPM packages to be installed globally:

- `eslint`
- `babel-eslint`
- `eslint-plugin-react`

```
npm install -g eslint babel-eslint eslint-plugin-react
```

We only require one `.eslintrc` in the root of our repo.

### Usage with Atom

Please install the Atom plugin [linter-eslint](https://atom.io/packages/linter-eslint).

0. Run `npm config get prefix` and paste the result path in the plugin settings under Global Node Path.
0. Enable the following in the plugin settings:
  0. `Disable When No Eslintrc File In Path`
  0. `Show Rule Id In Message`
  0. `Use Global Eslint`
0. Restart Atom and enjoy.
