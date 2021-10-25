tloulms, a theme for Open edX
======================================

.. image:: ./screenshots/01-landing-page.png
    :alt: Platform landing page


Installation
------------

Clone the theme repository::

    git clone https://github.com/mochenel/tloulms

Render your theme::

    tutor config render --extra-config ./tloulms/config.yml ./gugu/theme "$(tutor config printroot)/env/build/openedx/themes/tloulms"

Rebuild the Openedx docker image::

    tutor images build openedx

Restart your platform::

    tutor local start -d

You will then have to enable the "tloulms" theme
    tutor local settheme gugu localhost studio.localhost \
        $(tutor config printvalue LMS_HOST) $(tutor config printvalue CMS_HOST)

Upgrade
-------

To upgrade the gugu theme from a previous version, simply pull the changes from the git repository::

    cd tloulms/
    git pull

Then run the commands above starting from ``tutor config render...``.

Customization
-------------

Setting custom values
~~~~~~~~~~~~~~~~~~~~~

A few settings in the theme can be easily customised: this includes the theme primary color, landing page tagline, footer legal links. Theme settings are defined in the `config.yml <https://github.com/mochenel/tloulms/blob/master/config.yml>`__ file at the root of the repository. You can override all or part of those settings by creating you own ``config-custom.yml`` file. Then, render the theme with::

    tutor config render \
        --extra-config ./tloulms/config.yml \
        --extra-config ./tloulms/config-custom.yml \
        ./tloulms/theme "$(tutor config printroot)/env/build/openedx/themes/tloulms"

Changing the default logo and other images
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The theme images are stored in `tloulms/theme/lms/static/images <https://https://github.com/mochenel/tloulms/master/theme/lms/static/images>`__ for the LMS, and in `tloulms/theme/cms/static/images <https://github.com/mochenel/tloulms/tree/master/theme/cms/static/images>`__ for the CMS. To use custom images in your theme, just replace the files stored in these folders with your own prior to running ``tutor config render``.

