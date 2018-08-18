# blog-react-django
--------------------
## Use react and django (plugins: *django-webpack-loader* and *webpack-bundle-tracker*) to create a blog
### *Notes*
### 1. Install `django-webpack-loader` and insert `webpack_loader` to `INSTALLED_APPS`,add 
>`WEBPACK_LOADER = {
>  'DEFAULT': {
>    'BUNDLE_DIR_NAME': 'bundles/', 'STATS_FILE': os.path.join(BASE_DIR, 'webpack-stats.dev.json'),
>  }
>}` 
under settings.py.
### 2. Install `webpack-bundle-tracker --save-dev` in frontend(React Root Directory), modify
`module.exports = {
  // no change with other values
  statsRoot: resolveApp('../'),
}` in config/paths.js

