Описание API
=============

Все запросы работают через общий префикс

.. code-block:: text

   https://api.cloudcommerce.zd.ua/wms/v1

Тестовый ключ

.. code-block:: text

   https://api.cloudcommerce.zd.ua/wms/v1

.. http:get:: https://api.cloudcommerce.zd.ua/wms/v1/(string:MethodName)?APIKEY=(string:APIKEY)&(string:PARAMS)

    :query string MethodName:  наименование вызываемого метода
    :query string API_KEY:  уникальный ключ доступа
    :query string PARAMS: дополнительные параметры, разделяемые знаком & (зависит от метода)