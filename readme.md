Source: Khalilstemmler
# @Installing-Dependencies
1. Setup Node.js package.json\
    $ npm init -y 
2. Add typescript as a Dev dependency\
    $ npm install typescript --save-dev
3. Install ambient Node.js types for Typescript\
     $ npm install @types/node --save-dev
4. Create a tsconfig.json\
    $ npx tsc --init --rootDir src --outDir Dist --esModuleInterop --resolveJsonModule --lib es6 --module commonjs --allowJs true --noImplicitAny true

5. To compile our typescript file we can use\
	$ npx tsc

# @Cold-Reloading
1. $ npm install --save-dev ts-node nodemon
2. Add a nodemon.json config.\
    {
        "watch": ["src"],
        "ext": ".ts,.js",
        "ignore": [],
        "exec": "npx ts-node ./src/index.ts"
    }
3. Add a script to run "nodemon" to your package.json\
	   i. "start:dev": "npx nodemon"

# @Creating Production Builds
1. Install "rimraf" (similar to # rm -rf command)\
    $ npm install --save-dev rimraf
2. Add the following to your package.json.\
    i. "build": "rimraf ./dist && tsc", (When run, rimraf will remove your old build folder before the Typescript compiler emits new code to "dist".
3. Add startup script to package.json\
    i. "start": "npm run build && node dist/index.js".
