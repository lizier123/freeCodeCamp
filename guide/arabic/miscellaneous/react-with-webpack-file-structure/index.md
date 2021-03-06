---
title: React with Webpack File Structure
localeTitle: تتفاعل مع بنية ملف Webpack
---
الآن حان الوقت لإعداد هيكل الملف الخاص بنا قبل كتابة أي رمز.

أولاً ، دعنا ننشئ ملفًا جديدًا باسم `.gitignore` :

 `touch .gitignore 
` 

سيحتوي هذا الملف على قائمة بكافة الملفات والمجلدات التي **لن** يتم تضمينها عند دفع مشروعنا إلى GitHub. يوجد موقع ويب يخدم كود `.gitignore` لملفات `.gitignore` ، وهو أمر مفيد للغاية ، لأنه في كثير من الأحيان ، يمكن أن يكون ملف `.gitignore` طويلًا ومطولًا ، وقد ننسى بعض الملفات أو المجلدات التي نريد أن يتجاهلها Git.

انتقل إلى [https://www.gitignore.io/](https://www.gitignore.io/) واكتب `Node` في شريط البحث ، ثم انقر على " `Generate` . سيؤدي ذلك إلى إنشاء ملف يبدو كالتالي:

 `# Created by https://www.gitignore.io/api/node 
 
 ### Node ### 
 # Logs 
 logs 
 *.log 
 npm-debug.log* 
 
 # Runtime data 
 pids 
 *.pid 
 *.seed 
 
 # Directory for instrumented libs generated by jscoverage/JSCover 
 lib-cov 
 
 # Coverage directory used by tools like istanbul 
 coverage 
 
 # Grunt intermediate storage (http://gruntjs.com/creating-plugins#storing-task-files) 
 .grunt 
 
 # node-waf configuration 
 .lock-wscript 
 
 # Compiled binary addons (http://nodejs.org/api/addons.html) 
 build/Release 
 
 # Dependency directories 
 node_modules 
 jspm_packages 
 
 # Optional npm cache directory 
 .npm 
 
 # Optional REPL history 
 .node_repl_history 
` 

الآن يمكننا نسخ ولصق ذلك في ملف `.gitignore` بنا.

لاحظ أن `.gitignore` ملف يجب أن تتضمن دائما `node_modules` . هذا أمر في غاية الأهمية ، لأننا لا نريد تضمين مجلد `node_modules` بنا مع `node_modules` Git ، حيث أنها تستهلك مساحة كبيرة على القرص ، ويمكن تثبيتها بتثبيت `npm install` ، والذي يشير إلى `package.json` لدينا.

معظم الملفات والمجلدات المدرجة في ملف `.gitignore` بنا غير موجودة في مشروعنا حتى الآن ، ولكن إذا فعلت ذلك في المستقبل ، فلن يتم تضمينها في التزامات Git الخاصة بنا ، وهي مهمة ومفيدة ، لأننا يجب أن نكون انتقائي حول ما نرتكبه.

الآن ، نحتاج إلى إنشاء مجلد جديد يحتوي على محتويات شفرة **التطوير الخاصة** بنا. دعونا نسميها `src` :

 `mkdir src 
` 

بعد ذلك ، نحتاج إلى إنشاء مجلد يحتوي على ملفات نستخدمها لأغراض **الإنتاج** . سنسمي هذا المجلد `dist` :

 `mkdir dist 
` 

*   [مساعدة: مزيد من المعلومات حول `src` و `dist` المجلدات](http://stackoverflow.com/questions/23730882/what-is-the-role-of-src-and-dist-folders/23731040#23731040)

الآن بعد أن قمنا بتثبيت الحزم الخاصة بنا `dist` مجلدات `src` و `dist` فارغة ، ستبدو الشجرة كما هي (لا تشمل `.gitignore` ، وهو ملف مخفي):

 `. 
 ├── dist 
 ├── node_modules 
 ├── package.json 
 ├── src 
 └── webpack.config.js 
` 

الآن ، يمكننا إنشاء مجلد `js` جديد ينتقل إلى مجلد `src` بنا. سيحتوي هذا على جميع رموز التفاعل:

 `mkdir src/js 
` 

يمكننا المضي قدما وخلق `client.js` فارغة في `src/js` لدينا. سيكون هذا هو ملفنا الرئيسي React:

 `touch src/js/client.js 
` 

نحتاج أيضًا إلى `index.html` **لا يجب أن** يدخل مجلد `src` بنا ، بل إلى مجلد `dist` بنا ، لأنه مطلوب **لإنتاج** التطبيق لدينا:

 `touch dist/index.html 
` 

الآن ، تبدو شجرتنا بشيء من هذا القبيل:

 `. 
 ├── dist 
 │   └── index.html 
 ├── node_modules 
 ├── package.json 
 ├── src 
 │   └── js 
 │       └── client.js 
 └── webpack.config.js 
`