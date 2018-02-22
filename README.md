# Incorporating Compodoc
Generating project documentation for Angular's *Tour of Heroes* with [Compodoc](https://compodoc.github.io/website/)


## Install

I just did locally for now:
```
npm install --save-dev @compodoc/compodoc
```

Next you need to modify the *package.json* file to define a script task...
```
"scripts": {
  "compodoc": "./node_modules/.bin/compodoc -p tsconfig.json"
}
```
...and then run it:
```
npm run compodoc
```

After the run you should see the "COMPODOC" logo and logs as it reads through, ending with something like:
```
Documentation generated in ./documentation/ in 1.637 seconds using gitbook theme
```

Simply serve it and it should be hosted locally on 8080, open it automatically with:
```
compodoc -s --open
```





## Potential Issue

Path in my *package.json* was originally set to `...-p src/tsconfig.json` per the the documentation but it threw the error:
```
"/tsconfig.json" file was not found in the current directory
```
...so just remove `src/` and it should be accessible





## Additionally 
You do have the ability to add more scripts for generating documentation for
1. For generation
2. Serving
3. Or combining them

To do this, add additional npm scripts in the `package.json`:
```
...
"ng": "ng",
    "doc:build": "compodoc -p src/tsconfig.app.json",
    "doc:serve": "compodoc -s",
    "doc:buildandserve": "compodoc -p src/tsconfig.app.json -s",
    "start": "ng serve",
...
```
...then run
```
npm run doc:buildandserve
```
