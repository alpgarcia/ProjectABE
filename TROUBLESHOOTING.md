# npm install

```
➜  npm install

../../nan/nan_implementation_12_inl.h:103:42: error: no viable conversion from 'v8::Isolate *' to 'Local<v8::Context>'
  return scope.Escape(v8::Function::New( isolate
                                         ^~~~~~~
../../nan/nan_implementation_12_inl.h:337:37: error: too few arguments to function call, expected 2, have 1
  return v8::StringObject::New(value).As<v8::StringObject>();
         ~~~~~~~~~~~~~~~~~~~~~      ^

../../nan/nan_implementation_12_inl.h:337:58: error: expected '(' for function-style cast or type construction
  return v8::StringObject::New(value).As<v8::StringObject>();
                                         ~~~~~~~~~~~~~~~~^
../../nan/nan_implementation_12_inl.h:337:60: error: expected expression
  return v8::StringObject::New(value).As<v8::StringObject>();
                                                           ^
../../nan/nan.h:916:44: error: no matching member function for call to 'ToString'
      v8::Local<v8::String> string = from->ToString();
                                     ~~~~~~^~~~~~~~
../../nan/nan.h:926:37: error: cannot initialize a parameter of type 'v8::Isolate *' with an lvalue of type 'char *'
        length_ = string->WriteUtf8(str_, static_cast<int>(len), 0, flags);
                                    ^~~~
../../nan/nan_object_wrap.h:24:25: error: no member named 'IsNearDeath' in 'Nan::Persistent<v8::Object, v8::NonCopyablePersistentTraits<v8::Object> >'
    assert(persistent().IsNearDeath());
           ~~~~~~~~~~~~ ^

../../nan/nan_object_wrap.h:124:26: error: no member named 'IsNearDeath' in 'Nan::Persistent<v8::Object, v8::NonCopyablePersistentTraits<v8::Object> >'
    assert(wrap->handle_.IsNearDeath());
           ~~~~~~~~~~~~~ ^
/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX.sdk/usr/include/assert.h:93:25: note: expanded from macro 'assert'
    (__builtin_expect(!(e), 0) ? __assert_rtn(__func__, __FILE__, __LINE__, #e) : (void)0)
                        ^
../src/serialport.cpp:41:39: error: no matching member function for call to 'ToString'
  v8::String::Utf8Value path(info[0]->ToString());
                             ~~~~~~~~~^~~~~~~~

../src/serialport.cpp:48:44: error: no matching member function for call to 'ToObject'
  v8::Local<v8::Object> options = info[1]->ToObject();
                                  ~~~~~~~~~^~~~~~~~

../src/serialport.cpp:113:44: error: no matching member function for call to 'ToObject'
  v8::Local<v8::Object> options = info[1]->ToObject();
                                  ~~~~~~~~~^~~~~~~~

../src/serialport.cpp:250:44: error: no matching member function for call to 'ToObject'
  v8::Local<v8::Object> options = info[1]->ToObject();
                                  ~~~~~~~~~^~~~~~~~

../src/serialport.cpp:413:8: error: variable has incomplete type 'void'
  void init(v8::Handle<v8::Object> target) {
       ^
../src/serialport.cpp:413:34: error: expected '(' for function-style cast or type construction
  void init(v8::Handle<v8::Object> target) {
                       ~~~~~~~~~~^
../src/serialport.cpp:413:17: error: no member named 'Handle' in namespace 'v8'
  void init(v8::Handle<v8::Object> target) {
            ~~~~^
../src/serialport.cpp:413:36: error: use of undeclared identifier 'target'
  void init(v8::Handle<v8::Object> target) {
                                   ^
../src/serialport.cpp:413:43: error: expected ';' after top level declarator
  void init(v8::Handle<v8::Object> target) {
                                          ^
                                          ;
```

**Solution**: from https://github.com/rinormaloku/k8s-mastery/issues/23:

```
➜  npm install -g npm-check-updates
➜  npm-check-updates -u
➜  npm install
```

# gulp copy
```
➜  gulp copy
/Users/username/ProjectABE/node_modules/babelify/index.js:16
  throw err;
  ^

Error: Cannot find module '@babel/core'
Require stack:
...
 babelify@10 requires Babel 7.x (the package '@babel/core'). If you'd like to use Babel 6.x ('babel-core'), you should install 'babelify@8'.
    ...
  code: 'MODULE_NOT_FOUND',
  requireStack: [
    '/Users/username/ProjectABE/node_modules/babelify/index.js',
    '/Users/username/ProjectABE/gulpfile.js',
    '/usr/local/lib/node_modules/gulp-cli/lib/versioned/^4.0.0/index.js',
    '/usr/local/lib/node_modules/gulp-cli/index.js',
    '/usr/local/lib/node_modules/gulp-cli/bin/gulp.js'
  ]
}
```

**Solution**:
```
➜  sudo npm install --save-dev @babel/core @babel/preset-env
```

# Packaging your build as a MacOS App

* Build the project as described on [README.md](README.md#want-to-contribute) but use following command
instead of `gulp web-build`:
```
gulp nw-build
```
* Download NW.js from: https://nwjs.io/
* Follow the [latest official NW.js instructions](https://nwjs.readthedocs.io/en/latest/For%20Users/Package%20and%20Distribute/#package-option-1-plain-files-recommended). At the moment of writing this it was as simple as:
```
[...] put the files of your app into a folder named `app.nw` in `nwjs.app/Contents/Resources/ and done.
```
