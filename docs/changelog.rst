=========
Changelog
=========

v0.14.1
=======

Bug Fixes:

+ Cope with blank content encoding values in RPC Views
+ Unify all json handling functions into utils.JsonMixin

v0.14.0
=======

.. admonition:: WARNING: API breakage

   A large reorganisation of the code was undertaken.

   Now there are 3 major top-level modules:
   - serialiser
   - rest
   - rpc

Enhancements:

+ Added functional RPC system [merged from django-marionette]
+ Made most things accessible in top-level module

v0.13.9
=======

Enhancements:

+ Added Django 1.7 AppConfig, which will auto-discover on ready
+ Added a default implementation of ModelPublsiher.list_post_default
+ Tidied code with flake8

Bug Fixes:

+ Fixed use of wrong argument in auth.permit_groups

v0.13.8
=======

Enhancements:

+ Added prefetch_related and select_related support to ExportCsv action
+ Added Field.virtual to smooth changes to Field now raising AttributeError, and support optional fields

v0.13.7
=======

Enhancements:

+ Added ReadTheDocs, and prettied up the docs
+ Use Pythons content-type parsing
+ Added RPC publisher [WIP]
+ Allow api.register to be used as a decorator
+ Make Meta classes more proscriptive
+ Allow ModelSerialiser to override Field type used for fields.
+ Added ModelReadSerialiser and ModelCreateUpdateSerialiser to support more complex inflate scenarios [WIP]

Bug Fixes:

- Fixed ExportCsv and simplecsv extras
- Raise AttributeError if a deflating a field with no default set would result in using its default. [Fixes #28]
- Fixed auto-generated api_names.
- Purged under-developed ModelFormMixin class

v0.13.6
=======

Enhancements:

+ Overhauled testing
+ Added 'total_pages' to page meta.
+ Added Serialiser.obj_class

v0.13.5.1
=========

Bug Fixes:

- Fix fix for b'' from last release, to work in py2

v0.13.5
=======

Bug Fixes:

- Fix use of b'' for Py3.3 [thanks zzing]

Enhancements:

+ Add options to control patterns

v0.13.4
=======

Bug Fixes:

- Return http.NotFound instead of raising it

Enhancements:

+ Added views publisher
+ Updated docs
+ Re-added support for ujson, if installed
+ Tidied up with pyflakes/pylint
+ Added Publisher.response_class property

v0.13.3
=======

Bugs Fixed:

- Make API return NotFound, instead of Raising it
- Remove bogus CSV Reader class

v0.13.2.1
=========

Bugs Fixed:

- Fixed typo
- Fixed resolving cache in mixin

v0.13.2
=======

Enhancements:

+ Separate Publisher.build_view from Publisher.patterns to ease providing custom patterns
+ Added SimplePatternsMixin for Publisher
+ Added Publisher.sort_object_list and Publisher.filter_object_list hooks

v0.13.1
=======

Bugs Fixed:

- Fixed silly bug in inflate

v0.13.0
=======

.. admonition:: WARNING: API breakage

   Changed auto-discover to look for 'publishers' instead of 'seraliser'.

Enhancements:

+ Added Field.null support
+ Now use the Field.default value
+ ValidationError handled in all field and custom inflator methods

v0.12.5.1
=========

Bugs Fixed:

- Fix mistake introduced in 0.12.3 which broke NewRelic support

v0.12.5
=======

Bugs Fixed:

- Restored Django 1.4 compatibility

Enhancements:

+ Allow disabling of API introspection index

v0.12.4
=======

Bugs Fixed:

- Fixed filename generation in csv export action
- Fixed unicode/str issues with type() calls

Enhancements:

+ Split simplecsv and csv export into extras module
+ Merged engine class directly into Publisher
+ Added fields.StringField

v0.12.3
=======

Bugs Fixed:

- Fix argument handling in Model*SerialiserFields
- Tidied up with pyflakes

Enhancements:

+ Added support for Py3.3 [thanks ioneyed]
+ Overhauled the MetaSerialiser class
+ Overhauled "sandbox" app
+ Added csv export action

v0.12.2
=======

Enhancements:

+ Support read_only in modelserialiser_factory

v0.12.1
=======

Bugs Fixed:

- Flatten url patterns so object_default can match without trailing /
- Fix class returned in permit decorator [Thanks emilkjer]

Enhancements:

+ Allow passing an alternative default instead of None for Publisher.get_request_data
+ Added "read_only_fields" to ModelSerialiser [thanks jayant]

v0.12
=====

Enhancements:

+ Tune Serialisers to pre-build their deflater/inflater method lists, removing work from the inner loop
+ Remove \*args where it's no helpful

v0.11.6.1
=========

Bugs Fixed:

- Renamed HttpResponseRedirect to HttpResponseRedirection to avoid clashing with Django http class

v0.11.6
=======

Bugs Fixed:

- Raise a 404 on paginator raising EmptyPage, instead of failing

v0.11.5.1
=========

Bugs Fixed:

- Fix arguments passed to execute method

v0.11.5
=======

Enhancements:

+ Add Publisher.execute to make wrapping handler calls easier [also, makes NewRelic simpler to hook in]
+ Allow empty first pages in pagination
+ Added support module for NewRelic

v0.11.4
=======

Enhancements:

+ Make content-type detection more forgiving

v0.11.3
=======

Enhancements:

+ Make get_page honor limit parameter, but bound it to max_page_size, which defaults to page_size
+ Allow changing the GET param names for page, offset and limit
+ Allow passing page+limit or offset+limit

v0.11.2
=======

Enhancements:

+ Added BooleanField
+ Extended tests
+ Force CSRF protection

v0.11.1
=======

Enhancements:

+ Changed SerialiserField/ManySerialiserField to replace reduce/restore instead of overriding inflate/deflate methods
+ Fixed broken url pattern for object action
+ Updated fields documentation

v0.11
=====

.. admonition:: API breakage

    Serialiser.deflate_object and Serialiser.deflate_list have been renamed.

Enhancements:

+ Changed deflate_object and deflate_list to object_deflate and list_deflate to avoid potential field deflater name conflict
+ Moved all model related code to models.py
+ Added modelserialiser_factory
+ Updated ModelSerialiserField/ModelManySerialiserField to optionally auto-create a serialiser for the supplied model

v0.10.3
=======

Enhancements:

+ Added python2.6 support back [thanks nkuttler]
+ Added more documentation
+ Added Publisher.get_serialiser_kwargs hook
+ Publisher.get_data was renamed to Publisher.get_request_data for clarity

v0.10.2
=======

Bugs Fixed:

- Removed leftover debug print

v0.10.1
=======

Enhancements:

+ Added Publisher introspection
+ Added LocationHeaderMixin to HTTP classes

v0.10
=====

Bugs Fixed:

- Removed useless cruft form utils

Enhancements:

+ Replaced http subclasses with Exceptional ones
+ Wrap call to handlers to catch Exceptional http responses

v0.9.1
======

Enhancements:

+ Started documentation
+ Added permit_groups decorator
+ Minor speedup in MetaSerialiser

v0.9
====

Bugs Fixed:

- Fixed var name bug in ModelSerialiser.restore_object
- Removed old 'may' auth API

Enhancements:

+ Added permit decorators
+ use string formatting not join - it's slightly faster

v0.8
====

Enhancements:

+ Added create/delete methods to ModelPublisher
+ Renamed HttpResponse subclasses
+ Split out BasePublisher class
+ Added http.STATUS dict/list utility class

.. note::

   Because this uses OrderedDict nap is no longer python2.6 compatible


v0.7.1
======

Enhancements:

+ Use first engine.CONTENT_TYPES as default content type for responses

v0.7
====

Bugs Fixed:

- Removed custom JSON class

Enhancements:

+ Added Engine mixin classes
+ Added MsgPack support
+ Added type-casting fields

v0.6
====

Bugs Fixed:

- Fixed JSON serialising of date/datetime objects

Enhancements:

+ Added index view to API
+ Make render_single_object use create_response
+ Allow create_response to use a supplied response class

v0.5
====

Enhancements:

+ Added names to URL patterns
+ Added "argument" URL patterns

v0.4
====

Enhancements:

+ Added next/prev flags to list meta-data
+ Added tests

v0.3
====

Enhancements:

+ Changed to more generic extra arguments in Serialiser

v0.2
====

Bugs Fixed:

- Fixed bug in serialiser meta-class that broke inheritance
- Fixed variable names

Enhancements:

+ Pass the Publisher down into the Serialiser for more flexibility
+ Allow object IDs to be slugs
+ Handle case of empty request body with JSON content type
+ Added SerialiserField and ManySerialiserField
+ Added Api machinery
+ Changed Serialiser to use internal Meta class
+ Added ModelSerialiser class

v0.1
====

Enhancements:

+ Initial release, fraught with bugs :)

