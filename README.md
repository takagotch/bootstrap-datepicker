### bootstrap-datepicker
---
https://github.com/uxsolutions/bootstrap-datepicker

```
yarn global add grunt-cli
yarn install

npm install --global grunt-cli
npm install
```

```js
module.exports = function(grunt){
  'use strict';
  
  grunt.util.linefeed = '\n';
  
  grunt.initConfig({
    pkg: grunt.file.readJSON('package.json'),
    banner: [
      '/*!',
      ' * Datepicker for Bootstrap v<%= pkg.version %> (<%= pkg.homepage %>)',
      ' *',
      ' * Licensed under the Apache License v2.0 (http://www.apache.org/licenses/LICENSE-2.0)',
      ' */'
    ].join('\n') + '\n',
    
    clean:{
      dist: ['dist', '*-dist.zip']
    },
    jshint: {
      options: {
        jshintrc: 'js/.jshintrc'
      },
      main: {
        src: 'js/bootstrap-datepicker.js'
      },
      locales: {
        src: 'js/locales/*.js'
      },
      gruntfile: {
        options: {
          jshintrc: 'grunt/.jshintrc'
        },
        src: 'Gruntfile.js'
      }
    },
    jscs: {
      options: {
        config: 'js/.jscsrc'
      },
      main: {
        src: 'js/bootstrap-datepicker.js'
      },
      locales: {
        src: 'js/locales/*.js'
      },
      gruntfile: {
        src: 'Gruntfile.js'
      }
    },
    qunit: {
      main: 'tests/tests.html',
      timezone: 'tests/timezone.html',
      options: {
        console: false
      }
    },
    concat: {
      options: {
        stripeBanners: true
      },
      main: {
        src: 'js/bootstrap-datepicker.js',
        dest: 'dist/js/<%= pkg.name %>.js'
      }
    },
    uglify: {
      options: {
        preserveComments: 'some'
      },
      main: {
        src: '<%= concat.main.dest %>',
        dest: 'dist/js/<%= pkg.name %>.min.js'
      },
      locales: {
        files: [{
          expand: true,
          cwd: 'js/locales/',
          src: '*.js',
          dest: 'dist/locales/',
          rename: function(dest, name){
            return dest + name.replace(/\.js$/, '.min.js');
          }
        }]
      },
      
      
      
    }
  });
}
```

```
```

