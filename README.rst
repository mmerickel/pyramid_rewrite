pyramid_rewrite
===============

------------
Introduction
------------

pyramid_rewrite is a small extension for `Pyramid <http://www.pylonsproject.org/>`_ to rewrite urls before further processing takes place.

------------
Installation
------------

Just do

``pip install pyramid_rewrite``

or

``easy_install pyramid_rewrite``

-------------
Compatibility
-------------

pyramid_rewrite runs with pyramid>=1.3 and python>=2.6 and python>=3.2.
Other versions might also work.

-------------
Documentation
-------------

Usage example::

    def main(global_config, **settings):
        config = Configurator(settings=settings)
        config.include('pyramid_rewrite')
        # add url rewriting rules...
        #   first parameter is a regular expression
        #   second parameter is the target url
        config.add_rewrite_rule(r'/favicon.ico', r'/static/favicon.ico')
        config.add_rewrite_rule(r'/gallery/(?P<subpath>.*)',
                                r'/root/%(subpath)s')
        #
        # ... rest of configuration
        #
        # return WSGI application instance
        return config.make_wsgi_app()

Better documentation might follow.

