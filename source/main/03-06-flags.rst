Flags
=====

In this section, we will:

- Introduce flags
- How to use them with if statements

Introducing Flags
-----------------

In previous sections, enums were introduced, sets of related but mutually exclusive
values. In case you want to work with multiple values that are related to each other
without them being restricted to take a single value, you can use Flags.

A flag is a group of values that can be bound to each other to form a set of
that can later be processed and logically operate over them. Their declaration
is an ordinary enum declaration, just with the ``[Flags]`` attribute.

.. code-block:: vala

   [Flags]
   public enum WallpaperOptions {
      BACKGROUND,
      LOCKSCREEN,
      SCREEN_SAVER,
      SHOW_PREVIEW
   }

You can instantiate a flag like this:

.. code-block:: vala

   WallpaperOptions options = BACKGROUND;

To instantiate flags with more than one value, the ``|`` operator is used:

.. code-block:: vala

   WallpaperOptions options = BACKGROUND | LOCKSCREEN | SHOW_PREVIEW;
   // This flag instance is now using three values

Using Flags
-----------

To know which values of the flags are being used, you use ``if`` statements along
with the ``in`` keyword.

.. code-block:: vala

   [Flags]
   public enum WallpaperOptions {
      BACKGROUND,
      LOCKSCREEN,
      SCREEN_SAVER,
      SHOW_PREVIEW
   }

   public static void main () {
      WallpaperOptions options = BACKGROUND | LOCKSCREEN;

      if (BACKGROUND in options) {
         print ("The wallpaper has been set as Background Image\n")
      }

      if (LOCKSCREEN in options) {
         print ("The wallpaper has been set as Lockscreen Image\n")
      }

      if (SCREEN_SAVER in options) {
         print ("The wallpaper has been set as Screensaver\n")
      }

      if (SHOW_PREVIEW in options) {
         print ("A preview of the background image has been shown\n")
      }
   }

The program above will have the following output:

.. code-block::

   The wallpaper has been set as Background Image
   The wallpaper has been set as Lockscreen Image