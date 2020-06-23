To add to github use this guide: 

https://github.com/gitname/react-gh-pages

If you need to update React files etc. 

```
npm install

npm start

```

If get errors can do: 

```
npm audit fix

```

This will clean up but you'll probably get a note saying x vulnerabilities require manual review and mentioning breaking changes (i.e. changes may break app)

```
npm audit
```

will give idea of what issue are. 

Npm update will update to highest version possible (i.e. the minor release because ^ sign is used before version) without having breaking changes

```
npm update
```

Assumming changes look okay: 
```
npm audit fix --force
```
Push to github and check github security tab. 
