# Webapp Checklist

Detalles técnicos que el programador de una aplicación web debe considerar antes de publicar un sitio.

La idea aquí es que la mayoría de nosotros ya deberíamos saber la mayoría de lo que está en esta lista. Pero puede que haya uno o dos elementos que no hayas examinado antes, que no entiendas del todo o que nunca hayas escuchado.

## Interfaz y experiencia del usuario

* Ten en cuenta que los navegadores implementan estándares de forma incoherente y asegúrate de que tu sitio funcione razonablemente bien en los principales navegadores. Como mínimo, haz pruebas en el más reciente motor de renderizado [Gecko](https://es.wikipedia.org/wiki/Gecko_%28motor_de_renderizado%29h) ([Firefox](http://firefox.com/)), en WebKit ([Safari](http://www.apple.com/safari/) and some mobile browsers), [Chrome](http://www.google.com/chrome), los [navegadores IE](http://en.wikipedia.org/wiki/Internet_Explorer) que soportes (aproveche las [Imágenes VPC para la compatibilidad de aplicaciones](http://www.microsoft.com/Downloads/details.aspx?FamilyID=21eabb90-958f-4b64-b5f1-73d0a413c8ef&displaylang=en)), y [Opera](http://www.opera.com/). También considera cómo [los navegadores representan tu sitio](http://www.browsershots.org) en los diferentes sistemas operativos.
* Considera cómo las personas puedan usar el sitio desde navegadores diferentes a los principales navegadores: teléfonos celulares, lectores de pantalla y motores de búsqueda, por ejemplo. &mdash; Algo de información de accesibilidad: [WAI](http://www.w3.org/WAI/) y [Section508](http://www.section508.gov/), desarrollo móvil: [MobiForge](http://mobiforge.com/).
* Staging: cómo implementar actualizaciones sin afectar a sus usuarios. Tenga a su disposición uno o más entornos de pruebas o etapas para implementar cambios en la arquitectura, el código o el contenido crítico, y asegúrese de que se puedan implementar de forma controlada sin romper nada. Tenga una forma automatizada de implementar luego los cambios aprobados en el sitio en vivo. Esto se implementa más eficazmente junto con el uso de un sistema de control de versiones (CVS, Subversion, etc.) y un mecanismo de compilación automático (Ant, NAnt, etc.).
* No muestres errores técnicos directamente al usuario.
* No coloques las direcciones de correo electrónico de los usuarios en texto sin formato, ya que recibirán spam hasta la muerte.
* Agrega el atributo `rel="nofollow"` a los enlaces generados por el usuario [para evitar el spam](https://es.wikipedia.org/wiki/Nofollow).
* [Define límites bien analizados en tu sitio](http://www.codinghorror.com/blog/archives/001228.html). Esto también compete a la Seguridad.
* Aprende cómo hacer [Mejora progresiva](https://es.wikipedia.org/wiki/Mejora_progresiva).
* [Redirect After Post](https://es.wikipedia.org/wiki/Post/Redirect/Get) si ese envío fue exitoso, para evitar la actualización al volverse a enviar.
* No olvides tener en consideración a la Accesibilidad. Siempre es una buena idea y, en determinadas circunstancias, es un [requisito legal](http://www.section508.gov/). La [WAI-ARIA](http://www.w3.org/WAI/intro/aria) y la [WCAG 2](http://www.codexexempla.org/traducciones/pautas-accesibilidad-contenido-web-2.0.htm) son buenos recursos en este área.
* Lee el libro [No me hagas pensar](http://www.sensible.com/dmmt.html)


## Seguridad

* Es mucho para digerir, pero la [guía de desarrollo de OWASP](http://www.owasp.org/index.php/Category:OWASP_Guide_Project) cubre la seguridad de  sitios web de arriba a abajo.
* Conoce sobre Inyección (especialmente [Inyección SQL](http://en.wikipedia.org/wiki/SQL_injection)), y sobre cómo prevenirla.
* Nunca confíes en el ingreso de información por parte del usuario ni en ninguna otra cosa que venga en el request (¡que incluye cookies y valores de campos de formulario ocultos!).
* Encripta las contraseñas usando [salt](http://security.stackexchange.com/q/21263/396) y usa diferentes salts en tus filas para evitar ataques arco iris. Utiliza un algoritmo hash lento, como bcrypt (probado por el tiempo) o scrypt (más fuerte, pero más nuevo) ([1](http://www.tarsnap.com/scrypt.html), [2](http://it.slashdot.org/comments.pl?sid=1987632&cid=35149842)), para almacenar contraseñas. ([Cómo guardar una contraseña de forma segura](http://codahale.com/how-to-safely-store-a-password/)). El [NIST también aprueba PBKDF2 para encriptar contraseñas](http://security.stackexchange.com/q/7689/396), y está [aprobado por FIPS en .NET](http://security.stackexchange.com/ a / 2136/396) (más información [aquí](http://security.stackexchange.com/questions/211/how-to-securely-hash-passwords)). *Evita* usar la familia MD5 o SHA directamente.
* [No trates de crear tu fantástico sistema de autenticación](http://stackoverflow.com/questions/1581610/how-can-i-store-my-users-passwords-safely/1581919#1581919). Es tan fácil equivocarse en formas sutiles e incontrolables, y ni siquiera lo sabrías hasta _después_ de que seas hackeado.
* Conoce las [reglas para procesar tarjetas de crédito](https://www.pcisecuritystandards.org/). ([Mira esta pregunta también](http://stackoverflow.com/questions/51094/payment-processors-what-do-i-need-to-know-if-i-want-to-accept-credit-cards-on-m))
* Usa [SSL](http://www.mozilla.org/projects/security/pki/nss/ssl/draft302.txt)/[HTTPS](http://en.wikipedia.org/wiki/Https) para iniciios de sesión y en cualquier página donde se ingresen datos confidenciales (como información de tarjeta de crédito).
* [Previene el secuestro de la sesión](https://es.wikipedia.org/wiki/Secuestro_de_sesi%C3%B3n#Prevenci%C3%B3n).
* Evita el [cross site scripting](https://es.wikipedia.org/wiki/Cross-site_scripting) (XSS).
* Evita el [cross site request forgeries](https://es.wikipedia.org/wiki/Cross-site_request_forgery) (CSRF).
* Evita el [clickjacking](https://es.wikipedia.org/wiki/Clickjacking).
* Mantén tu sistema actualizado con los últimos parches.
* Asegúrate de que la información de conexión de tu base de datos esté segura.
* Mantente informado sobre las últimas vulnerabilidades y técnicas de ataque afectando a tu plataforma.
* Lee el [Browser Security Handbook](http://code.google.com/p/browsersec/wiki/Main) de Google.
* Lee [The Web Application Hacker's Handbook](http://amzn.com/0470170778).
* Considera el [Principio de mínimo privilegio](https://es.wikipedia.org/wiki/Principio_de_m%C3%ADnimo_privilegio). Trata de correr tu servidor de aplicaciones [como no-root](http://security.stackexchange.com/questions/47576/do-simple-linux-servers-really-need-a-non-root-user-for-security-reasons). ([Ejemplo de Tomcat](http://tomcat.apache.org/tomcat-8.0-doc/security-howto.html#Non-Tomcat_settings))


## Performance

* Implement caching if necessary, understand and use [HTTP caching](http://www.mnot.net/cache_docs/) properly as well as [HTML5 Manifest](http://www.w3.org/TR/2011/WD-html5-20110525/offline.html).
* Optimize images - don't use a 20 KB image for a repeating background.
* Learn how to [gzip/deflate content](http://developer.yahoo.com/performance/rules.html#gzip"gzipcontent") (<strike>[deflate is better](http://stackoverflow.com/questions/1574168/gzip-vs-deflate-zlib-revisited)</strike>).
* Combine/concatenate multiple stylesheets or multiple script files to reduce number of browser connections and improve gzip ability to compress duplications between files.
* Take a look at the [Yahoo Exceptional Performance](http://developer.yahoo.com/performance/) site, lots of great guidelines, including improving front-end performance and their [YSlow](http://developer.yahoo.com/yslow/) tool (requires Firefox, Safari, Chrome or Opera). Also, [Google page speed](https://developers.google.com/speed/docs/best-practices/rules_intro) (use with [browser extension](https://developers.google.com/speed/pagespeed/insights_extensions)) is another tool for performance profiling, and it optimizes your images too.
* Use [CSS Image Sprites](http://alistapart.com/articles/sprites) for small related images like toolbars (see the "minimize HTTP requests" point)
* Busy web sites should consider [splitting components across domains](http://developer.yahoo.com/performance/rules.html#split).  Specifically...
* Static content (i.e. images, CSS, JavaScript, and generally content that doesn't need access to cookies) should go in a separate domain _[that does not use cookies](http://blog.stackoverflow.com/2009/08/a-few-speed-improvements/)_, because all cookies for a domain and its subdomains are sent with every request to the domain and its subdomains.  One good option here is to use a Content Delivery Network (CDN), but consider the case where that CDN may fail by including alternative CDNs, or local copies that can be served instead.
* Minimize the total number of HTTP requests required for a browser to render the page.
* Utilize [Google Closure Compiler](http://developers.google.com/closure/compiler/) for JavaScript and [other minification tools](http://developer.yahoo.com/yui/compressor/).
* Make sure there’s a `favicon.ico` file in the root of the site, i.e. `/favicon.ico`. [Browsers will automatically request it](http://mathiasbynens.be/notes/rel-shortcut-icon), even if the icon isn’t mentioned in the HTML at all. If you don’t have a `/favicon.ico`, this will result in a lot of 404s, draining your server’s bandwidth.


## SEO (Search Engine Optimization)

* Use "search engine friendly" URLs, i.e. use `example.com/pages/45-article-title` instead of `example.com/index.php?page=45`
* When using `#` for dynamic content change the `#` to `#!` and then on the server `$_REQUEST["_escaped_fragment_"]` is what googlebot uses instead of `#!`. In other words, `./#!page=1` becomes `./?_escaped_fragments_=page=1`. Also, for users that may be using FF.b4 or Chromium, `history.pushState({"foo":"bar"}, "About", "./?page=1");` Is a great command. So even though the address bar has changed the page does not reload. This allows you to use `?` instead of `#!` to keep dynamic content and also tell the server when you email the link that we are after this page, and the AJAX does not need to make another extra request.
* Don't use links that say ["click here"](http://ux.stackexchange.com/questions/12100/why-shouldnt-we-use-the-word-here-in-a-textlink). You're wasting an SEO opportunity and it makes things harder for people with screen readers.
* Have an [XML sitemap](http://www.sitemaps.org/), preferably in the default location `/sitemap.xml`.
* Use [`<link rel="canonical" ... />`](http://googlewebmastercentral.blogspot.com/2009/02/specify-your-canonical.html) when you have multiple URLs that point to the same content, this issue can also be addressed from [Google Webmaster Tools](http://www.google.com/webmasters/).
* Use [Google Webmaster Tools](http://www.google.com/webmasters/) and [Bing Webmaster Tools](http://www.bing.com/toolbox/webmaster).
* Install [Google Analytics](http://www.google.com/analytics/) right at the start (or an open source analysis tool like [Piwik](http://piwik.org/)).
* Know how [robots.txt](http://en.wikipedia.org/wiki/Robots_exclusion_standard) and search engine spiders work.
* Redirect requests (using `301 Moved Permanently`) asking for `www.example.com` to `example.com` (or the other way round) to prevent splitting  the google ranking between both sites.
* Know that there can be badly-behaved spiders out there.
* If you have non-text content look into Google's sitemap extensions for video etc. There is some good information about this in [Tim Farley's answer](http://stackoverflow.com/questions/72394/what-should-a-developer-know-before-building-a-public-web-site#167608).


## Technology

 * Understand [HTTP](http://www.ietf.org/rfc/rfc2616.txt) and things like GET, POST, sessions, cookies, and what it means to be "stateless".
 * Write your [XHTML](http://www.w3.org/TR/xhtml1/)/[HTML](http://www.w3.org/TR/REC-html40/) and [CSS](http://www.w3.org/TR/CSS2/) according to the [W3C specifications](http://www.w3.org/TR/) and make sure they [validate](http://validator.w3.org/).  The goal here is to avoid browser quirks modes and as a bonus make it much easier to work with non-traditional browsers like screen readers and mobile devices.
 * Understand how JavaScript is processed in the browser.
 * Understand how JavaScript, style sheets, and other resources used by your page are loaded and consider their impact on *perceived* performance. It is now widely regarded as appropriate to [move scripts to the bottom](http://developer.yahoo.com/blogs/ydn/posts/2007/07/high_performanc_5/) of your pages with exceptions typically being things like analytics apps or HTML5 shims.
 * Understand how the JavaScript sandbox works, especially if you intend to use iframes.
 * Be aware that JavaScript can and will be disabled, and that AJAX is therefore an extension, not a baseline.  Even if most normal users leave it on now, remember that [NoScript](http://noscript.net/) is becoming more popular, mobile devices may not work as expected, and Google won't run most of your JavaScript when indexing the site.
 * Learn the [difference between 301 and 302 redirects](http://www.bigoakinc.com/blog/when-to-use-a-301-vs-302-redirect/) (this is also an SEO issue).
 * Learn as much as you possibly can about your deployment platform.
 * Consider using a [Reset Style Sheet](http://stackoverflow.com/questions/167531/is-it-ok-to-use-a-css-reset-stylesheet) or [normalize.css](http://necolas.github.com/normalize.css/).
 * Consider JavaScript frameworks (such as [jQuery](http://jquery.com/), [MooTools](http://mootools.net/), [Prototype](http://www.prototypejs.org/), [Dojo](http://dojotoolkit.org) or [YUI 3](http://yuilibrary.com/)), which will hide a lot of the browser differences when using JavaScript for DOM manipulation.
 * Taking perceived performance and JS frameworks together, consider using a service such as the [Google Libraries API](http://developers.google.com/speed/libraries/devguide) to load frameworks so that a browser can use a copy of the framework it has already cached rather than downloading a duplicate copy from your site.
 * Don't reinvent the wheel. Before doing ANYTHING search for a component or example on how to do it. There is a 99% chance that someone has done it and released an OSS version of the code.
 * On the flipside of that, don't start with 20 libraries before you've even decided what your needs are. Particularly on the client-side web where it's almost always ultimately more important to keep things lightweight, fast, and flexible.


## Bug fixing

* Understand you'll spend 20% of your time coding and 80% of it maintaining, so code accordingly.
* Set up a good error reporting solution.
* Have a system for people to contact you with suggestions and criticisms.
* Document how the application works for future support staff and people performing maintenance.
* Make frequent backups! (And make sure those backups are functional) Have a restore strategy, not just a backup strategy.
* Use a version control system to store your files, such as [Subversion](http://subversion.apache.org/), [Mercurial](http://mercurial.selenic.com/) or [Git](http://git-scm.org).
* Don't forget to do your Acceptance Testing.  Frameworks like [Selenium](http://seleniumhq.org/) can help. Especially if you fully automate your testing, perhaps by using a Continuous Integration tool, such as [Jenkins](http://jenkins-ci.org/) or [Drone](https://drone.io/).
* Make sure you have sufficient logging in place using frameworks such as [log4j](http://logging.apache.org/log4j/), [log4net](http://logging.apache.org/log4net/) or [log4r](http://log4r.rubyforge.org/). If something goes wrong on your live site, you'll need a way of finding out what.
* When logging make sure you capture both handled exceptions, and unhandled exceptions. Report/analyse the log output, as it'll show you where the key issues are in your site.


## Other

* Implement both server-side and client-side monitoring and analytics (one should be proactive rather than reactive).
* Use services like [UserVoice](https://www.uservoice.com/) and [Intercom](https://www.intercom.io/) (or any other similar tools) to constantly keep in touch with your users.
* Follow [Vincent Driessen](http://nvie.com/about/)'s [Git branching model](http://nvie.com/posts/a-successful-git-branching-model/)


# Disclaimer

This was originally a question asked on [Programmers-StackExchange](http://programmers.stackexchange.com/questions/46716/what-technical-details-should-a-programmer-of-a-web-application-consider-before)  by [Joel Coehoorn](http://programmers.stackexchange.com/users/8057/joel-coehoorn) and has since been [answered](http://programmers.stackexchange.com/a/46760/54643) and [maintained](http://programmers.stackexchange.com/posts/46760/revisions) as community wiki.

There are three reasons why I am making a GitHub repo:

1. Collaborative editing is much more powerful on GitHub.
2. People can fork this repo and make customizations that might not apply to everyone else.
3. We can have translations of the answer in many languages. Not everyone is good with English.


# Question

What things should a programmer implementing the technical details of a web application consider before making the site public? If Jeff Atwood can forget about HttpOnly cookies, sitemaps, and cross-site request forgeries all in the same site, what important thing could I be forgetting as well?

I'm thinking about this from a web developer's perspective, such that someone else is creating the actual design and content for the site. So while usability and content may be more important than the platform, you the programmer have little say in that. What you do need to worry about is that your implementation of the platform is stable, performs well, is secure, and meets any other business goals (like not cost too much, take too long to build, and rank as well with Google as the content supports).

Think of this from the perspective of a developer who's done some work for intranet-type applications in a fairly trusted environment, and is about to have his first shot and putting out a potentially popular site for the entire big bad world wide web.

Also, I'm looking for something more specific than just a vague "web standards" response. I mean, HTML, JavaScript, and CSS over HTTP are pretty much a given, especially when I've already specified that you're a professional web developer. So going beyond that, Which standards? In what circumstances, and why? Provide a link to the standard's specification.
