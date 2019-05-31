# create-react-app
` ``Record a create-react-app trip I took
I just wanted to build a small project and test something small, but it got really bumpy!

1, npx create-react-app my-app, yarn eject, (Just me)
2,
mobx 
mobx-react 
antd 
axios 
react-router-dom 
mockjs 
koa2 
koa-router 
query-string
busboy
path
fs
less less-loader
moment
(.....and so on)
3, I don't like style.module.css, so I change my webpack
// style files regexes
const cssRegex = /\.css$/;
// const cssModuleRegex = /\.module\.css$/;
const cssModuleRegex = /\.css$/;
const sassRegex = /\.(scss|sass)$/;
// const sassModuleRegex = /\.module\.(scss|sass)$/;
const sassModuleRegex = /\.(scss|sass)$/;
const lessRegex = /\.less$/;
const lessModuleRegex = /\.less$/;
{
  test: lessRegex,
  exclude: [/src/],
  use: getStyleLoaders(
    {
      importLoaders: 3,
      sourceMap: isEnvProduction && shouldUseSourceMap
    },
    'less-loader'
  ),
  sideEffects: true,
},
{
  test: lessModuleRegex,
  include: [/src/],
  use: getStyleLoaders(
    {
      importLoaders: 3,
      sourceMap: isEnvProduction && shouldUseSourceMap,
      modules: true,
      getLocalIdent: getCSSModuleLocalIdent
    },
    'less-loader'
  ),
},

Notices: getStyleLoaders 
if (preProcessor) {
      loaders.push({
        loader: require.resolve(preProcessor),
        options: {
          sourceMap: isEnvProduction && shouldUseSourceMap,
          javascriptEnabled: true   //add this code for antd's less
        },
      });
    }
   
4, add some alias for my directory
alias: {
    utils: path.resolve(__dirname, '../src/utils'),
    pages: path.resolve(__dirname, '../src/pages'),
    components: path.resolve(__dirname, '../src/components'),
    assets: path.resolve(__dirname, '../src/assets'),
    services: path.resolve(__dirname, '../src/utils'),
    store: path.resolve(__dirname, '../src/store'),
    routes: path.resolve(__dirname, '../src/routes'),
    'react-native': 'react-native-web',
  },
  
  5, .babelrc
  {
  "presets": [
    [
      "@babel/preset-env",
    ],
    [
      "@babel/preset-react"
    ]
  ],
  "plugins": [
    [
      "@babel/plugin-transform-runtime",
      {
        "corejs": false,
        "helpers": true,
        "regenerator": true,
        "useESModules": false
      }
    ],
    ["import", { "libraryName": "antd", "libraryDirectory": "es", "style": true }], 
    "@babel/plugin-syntax-dynamic-import",
    "@babel/plugin-syntax-import-meta",
    "@babel/plugin-proposal-json-strings",
    [
      "@babel/plugin-proposal-decorators",
      {
        "legacy": true
      }
    ],
    [
      "@babel/plugin-proposal-class-properties",
      {
        "loose": true
      }
    ],
    "@babel/plugin-proposal-function-sent",
    "@babel/plugin-proposal-export-default-from",
    "@babel/plugin-proposal-export-namespace-from",
    "@babel/plugin-proposal-numeric-separator",
    "@babel/plugin-proposal-throw-expressions",
    "@babel/plugin-transform-modules-commonjs",
    "@babel/plugin-transform-async-to-generator"
  ]
}
6, I hit this file package.json
{
  "name": "my-app",
  "version": "0.1.0",
  "private": true,
  "dependencies": {
    "@babel/cli": "^7.4.4",
    "@babel/core": "7.4.3",
    "@babel/node": "^7.4.5",
    "@babel/plugin-proposal-decorators": "^7.4.4",
    "@babel/plugin-proposal-export-default-from": "^7.2.0",
    "@babel/plugin-proposal-export-namespace-from": "^7.2.0",
    "@babel/plugin-proposal-function-sent": "^7.2.0",
    "@babel/plugin-proposal-numeric-separator": "^7.2.0",
    "@babel/plugin-proposal-throw-expressions": "^7.2.0",
    "@babel/plugin-syntax-dynamic-import": "^7.2.0",
    "@babel/plugin-syntax-import-meta": "^7.2.0",
    "@babel/plugin-transform-async-to-generator": "^7.4.4",
    "@babel/plugin-transform-modules-commonjs": "^7.4.4",
    "@babel/plugin-transform-react-jsx-self": "^7.2.0",
    "@babel/plugin-transform-react-jsx-source": "^7.2.0",
    "@babel/plugin-transform-runtime": "^7.4.4",
    "@babel/polyfill": "^7.4.4",
    "@babel/preset-env": "^7.4.5",
    "@babel/register": "^7.4.4",
    "@babel/runtime": "^7.4.5",
    "@svgr/webpack": "4.1.0",
    "antd": "^3.19.1",
    "axios": "^0.18.0",
    "babel-eslint": "10.0.1",
    "babel-jest": "^24.8.0",
    "babel-loader": "8.0.5",
    "babel-plugin-import": "^1.11.2",
    "babel-plugin-named-asset-import": "^0.3.2",
    "babel-preset-react-app": "^9.0.0",
    "busboy": "^0.3.1",
    "camelcase": "^5.2.0",
    "case-sensitive-paths-webpack-plugin": "2.2.0",
    "css-loader": "2.1.1",
    "dotenv": "6.2.0",
    "dotenv-expand": "4.2.0",
    "eslint": "^5.16.0",
    "eslint-config-react-app": "^4.0.1",
    "eslint-loader": "2.1.2",
    "eslint-plugin-flowtype": "2.50.1",
    "eslint-plugin-import": "2.16.0",
    "eslint-plugin-jsx-a11y": "6.2.1",
    "eslint-plugin-react": "7.12.4",
    "eslint-plugin-react-hooks": "^1.5.0",
    "file-loader": "3.0.1",
    "fs-extra": "7.0.1",
    "html-webpack-plugin": "^4.0.0-beta.5",
    "identity-obj-proxy": "3.0.0",
    "is-wsl": "^1.1.0",
    "jest": "24.7.1",
    "jest-environment-jsdom-fourteen": "0.1.0",
    "jest-resolve": "24.7.1",
    "jest-watch-typeahead": "0.3.0",
    "koa-bodyparser": "^4.2.1",
    "koa-router": "^7.4.0",
    "koa2": "^2.0.0-alpha.7",
    "koa2-cors": "^2.0.6",
    "less": "^3.9.0",
    "less-loader": "^5.0.0",
    "mini-css-extract-plugin": "0.5.0",
    "mobx": "^5.9.4",
    "mobx-react": "^6.0.2",
    "mockjs": "^1.0.1-beta3",
    "moment": "^2.24.0",
    "optimize-css-assets-webpack-plugin": "5.0.1",
    "pnp-webpack-plugin": "1.2.1",
    "postcss-flexbugs-fixes": "^4.1.0",
    "postcss-loader": "^3.0.0",
    "postcss-normalize": "^7.0.1",
    "postcss-preset-env": "^6.6.0",
    "postcss-safe-parser": "^4.0.1",
    "query-string": "^6.5.0",
    "react": "^16.8.6",
    "react-app-polyfill": "^1.0.1",
    "react-dev-utils": "^9.0.1",
    "react-dom": "^16.8.6",
    "react-router-dom": "^5.0.0",
    "resolve": "1.10.0",
    "sass-loader": "7.1.0",
    "semver": "6.0.0",
    "style-loader": "0.23.1",
    "terser-webpack-plugin": "1.2.3",
    "ts-pnp": "1.1.2",
    "url-loader": "1.1.2",
    "util": "^0.12.0",
    "webpack": "4.29.6",
    "webpack-dev-server": "3.2.1",
    "webpack-manifest-plugin": "2.0.4",
    "workbox-webpack-plugin": "4.2.0"
  },
  "scripts": {
    "start": "node scripts/start.js",
    "build": "node scripts/build.js",
    "test": "node scripts/test.js",
    "mock": "babel-node scripts/server.js"
  },
  "eslintConfig": {
    "extends": "react-app"
  },
  "browserslist": {
    "production": [
      ">0.2%",
      "not dead",
      "not op_mini all"
    ],
    "development": [
      "last 1 chrome version",
      "last 1 firefox version",
      "last 1 safari version"
    ]
  },
  "jest": {
    "collectCoverageFrom": [
      "src/**/*.{js,jsx,ts,tsx}",
      "!src/**/*.d.ts"
    ],
    "setupFiles": [
      "react-app-polyfill/jsdom"
    ],
    "setupFilesAfterEnv": [],
    "testMatch": [
      "<rootDir>/src/**/__tests__/**/*.{js,jsx,ts,tsx}",
      "<rootDir>/src/**/*.{spec,test}.{js,jsx,ts,tsx}"
    ],
    "testEnvironment": "jest-environment-jsdom-fourteen",
    "transform": {
      "^.+\\.(js|jsx|ts|tsx)$": "<rootDir>/node_modules/babel-jest",
      "^.+\\.css$": "<rootDir>/config/jest/cssTransform.js",
      "^(?!.*\\.(js|jsx|ts|tsx|css|json)$)": "<rootDir>/config/jest/fileTransform.js"
    },
    "transformIgnorePatterns": [
      "[/\\\\]node_modules[/\\\\].+\\.(js|jsx|ts|tsx)$",
      "^.+\\.module\\.(css|sass|scss)$"
    ],
    "modulePaths": [],
    "moduleNameMapper": {
      "^react-native$": "react-native-web",
      "^.+\\.module\\.(css|sass|scss)$": "identity-obj-proxy"
    },
    "moduleFileExtensions": [
      "web.js",
      "js",
      "web.ts",
      "ts",
      "web.tsx",
      "tsx",
      "json",
      "web.jsx",
      "jsx",
      "node"
    ],
    "watchPlugins": [
      "jest-watch-typeahead/filename",
      "jest-watch-typeahead/testname"
    ]
  },
  "proxy": "http://localhost:3002"
}



7, ok, this is my love, 
server.js  It can be run by yarn mock ("mock": "babel-node scripts/server.js") It's very important
import Koa from 'koa2';
import cors from 'koa2-cors';
import bodyParser from 'koa-bodyparser';
import base from '../config/base'
import router from '../server/mock';
const app = new Koa();
app.use(bodyParser());
app.use(router.routes()).use(router.allowedMethods())
app.use(cors());
app.listen(base.mock.port, () => {
  console.log(`The server is running at http://localhost:${base.mock.port}`)
});


My little demo can test file uploads, implement some mock interfaces, and of course, that's not all the code, so I'm going to push the rest of the code in the future, and if you happen to see it, don't go, just slap it or fork it; thanks` ``
