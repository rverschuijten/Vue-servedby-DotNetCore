# VueCoreBaseApp



Starting from the default ASPNET Core Angular application:

1. install npm package: `Vue Cli MiddleWare`
   install npm package; `Microsoft.AspNetCore.SpaServices.Extensions`
    
2. Go to Startup.cs
  change spa.UseAngular to 
  `spa.UseVueCli(npmScript: "serve", port: 8080);
                    // if you just prefer to proxy requests from client app, use proxy to SPA dev server instead:
                    // app should be already running before starting a .NET client
                    // spa.UseProxyToSpaDevelopmentServer("http://localhost:8080"); // your Vue app port
                    `
  
3. Delete ClientApp Folder
4. Open powershell in project root
5. Enter Command `vue create -n -b client-app`
6. Set Typescript build to - Use latest available
7. open projectname.csproj, edit `ClientApp` to `client-app`
8. start debug

If error occurs:
https://github.com/SoftwareAteliers/asp-net-core-vue-starter/issues/3

ps;
add new file  `tsconfig.json` in client-app
contents:
`{
  "compilerOptions": {
    "target": "esnext",
    "module": "esnext",
    "strict": true,
    "jsx": "preserve",
    "importHelpers": true,
    "moduleResolution": "node",
    "experimentalDecorators": true,
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true,
    "sourceMap": true,
    "baseUrl": ".",
    "types": [
      "node",
      "vuetify"
    ],
    "paths": {
      "@/*": [
        "src/*"
      ]
    },
    "lib": [
      "esnext",
      "dom",
      "dom.iterable",
      "scripthost"
    ]
  },
  "include": [
    "src/**/*.ts",
    "src/**/*.tsx",
    "src/**/*.vue",
    "tests/**/*.ts",
    "tests/**/*.tsx"
  ],
  "exclude": [
    "node_modules"
  ]
}`

*Typescript:*
- install `npm add typscript` and/or `npm add eslint`
- edit .csproj file and add
`  <ItemGroup>`
`    <Content Include="ClientApp\tsconfig.json" />`
`  </ItemGroup>`


For more info and tips try:
https://wildermuth.com/2019/04/08/Using-Vue-CLI-Inside-an-ASP-NET-Core-Project



Setup Vue pages:
1. Add folder `views` and `components`
2. Add `HelloWorld.vue`in views


vue add axios
Error cors:
https://medium.com/js-dojo/how-to-deal-with-cors-error-on-vue-cli-3-d78c024ce8d3
1. create `vue.config.js` next to `package.json`
Contents:
**module.exports = {
  // options...
    devServer: {
        proxy: 'http://localhost:54259/',
    }
}**
