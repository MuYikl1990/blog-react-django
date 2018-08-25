# blog-react-django
--------------------
## Use react and django (plugins: *django-webpack-loader* and *webpack-bundle-tracker*) to create a blog (*node_modules* in the .gitignore file)
### *Notes:*
### 1. Install `django-webpack-loader` and insert `webpack_loader` to `INSTALLED_APPS`,add 
        
        WEBPACK_LOADER = {
          'DEFAULT': {
            'BUNDLE_DIR_NAME': 'bundles/', 'STATS_FILE': os.path.join(BASE_DIR, 'webpack-stats.dev.json'),
          }
        }
###     under settings.py.

### 2. Install `webpack-bundle-tracker --save-dev` in frontend(React Root Directory), modify
        module.exports = {
          // no change with other values
          statsRoot: resolveApp('../'),
       }
###     in config/paths.js.
### 3. Change *const publicPath = 'http://localhost:3000/'* and  *const publicUrl = 'http://localhost:3000/'*, and import plugin use
###     `const BundleTracker = require(webpack-bundle-tracker)`, then modify 
        module.exports = {
           entry: [
               //keep other values
               require.resolve('webpack-dev-server/client') + '?http://localhost:3000',
                require.resolve('webpack/hot/dev-server'),
               //require.resolve('react-dev-utils/webpackHotDevClient'),
           ],
           plugins:[
               //keep other values
               new BundleTracker({path: paths.statsRoot, filename: 'webpack-stats.dev.json'}),
           ]
        }
###     in config/webpack.config.dev.js.
### Finally, any change will show on http://127.0.0.1:8000 via modify src/App.js.

