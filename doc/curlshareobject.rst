.. _curlshareobject:

CurlShare Object
================

.. autoclass:: pycurl.CurlShare

    CurlShare objects have the following methods:

    .. method:: close() -> None

        Corresponds to `curl_share_cleanup`_ in libcurl. This method is
        automatically called by pycurl when a CurlShare object no longer has
        any references to it, but can also be called explicitly.

    .. method:: setopt(option, value) -> None

        Corresponds to `curl_share_setopt`_ in libcurl, where *option* is
        specified with the ``CURLSHOPT_*`` constants in libcurl, except that the
        ``CURLSHOPT_`` prefix has been changed to ``SH_``. Currently, *value* must be
        either ``LOCK_DATA_COOKIE`` or ``LOCK_DATA_DNS``.

        Example usage:

        ::

            import pycurl
            curl = pycurl.Curl()
            s = pycurl.CurlShare()
            s.setopt(pycurl.SH_SHARE, pycurl.LOCK_DATA_COOKIE)
            s.setopt(pycurl.SH_SHARE, pycurl.LOCK_DATA_DNS)
            curl.setopt(pycurl.URL, 'http://curl.haxx.se')
            curl.setopt(pycurl.SHARE, s)
            curl.perform()
            curl.close()

.. _curl_share_cleanup:
    http://curl.haxx.se/libcurl/c/curl_share_cleanup.html
.. _curl_share_setopt:
    http://curl.haxx.se/libcurl/c/curl_share_setopt.html
