Справочники
=============

Не зависимые от ключа справочники (общие):

* DeliveryTypeList
* PackTypeList
* MeasurementUnitList
* TZoneList


Зависимые от ключа справочники:

* QualityList
* GoodsList
* GoodsGroupList
* PackagingList
* GoodsSpecificationList (еще не опубликован метод доступа)
* WarehouseList (скоро будет зависимым от ключа, в связи с открытием дополнительного склада)


QualityList
--------------

Метод используется для получение перечня групп и типов качества товара.

.. http:get:: https://api.cloudcommerce.zd.ua/wms/v1/QualityList?APIKEY=(int:APIKEY)


    **Example request**:

    .. tabs::

        .. code-tab:: bash

            $ curl https://api.cloudcommerce.zd.ua/wms/v1/QualityList?APIKEY=83F5428CBAE296FFE0509CB9CB2A24EB

        .. code-tab:: python

            import requests
            URL = 'https://api.cloudcommerce.zd.ua/wms/v1/QualityList?APIKEY=83F5428CBAE296FFE0509CB9CB2A24EB'
            response = requests.get(URL)
            print(response.json())

    **Example response**:

    .. sourcecode:: json

        {
          "response": {
            "quality": [
              {
                "p_id": "1",
                "p_name": "Кондиция",
                "p_stype": "1"
              },
              {
                "p_id": "4",
                "p_name": "Брак",
                "p_stype": "2"
              }
            ]
          },
          "status": {
            "code": "ok"
          }
        }

    :>json integer p_id: код группы качества
    :>json string p_name: наименование группы качества
    :>json integer p_stype: тип качества


DeliveryTypeList
-----------------

Метод используется для получения списка доступных способов доставки заказов - самовывозом, курьерскими службами (с интеграцией и без).


.. http:get:: https://api.cloudcommerce.zd.ua/wms/v1/DeliveryTypeList?APIKEY=(int:APIKEY)


    **Example request**:

    .. tabs::

        .. code-tab:: bash

            $ curl https://api.cloudcommerce.zd.ua/wms/v1/DeliveryTypeList?APIKEY=83F5428CBAE296FFE0509CB9CB2A24EB

        .. code-tab:: python

            import requests
            URL = 'https://api.cloudcommerce.zd.ua/wms/v1/DeliveryTypeList?APIKEY=83F5428CBAE296FFE0509CB9CB2A24EB'
            response = requests.get(URL)
            print(response.json())

    **Example response**:

    .. sourcecode:: json

        {
          "response": {
            "delivery_type": [
              {
                "p_id": "1",
                "p_name": "Самовивіз"
              },
              {
                "p_id": "2",
                "p_name": "Укрпошта"
              },
              {
                "p_id": "3",
                "p_name": "Джастін"
              },
              {
                "p_id": "4",
                "p_name": "Нова Пошта"
              },
              {
                "p_id": "5",
                "p_name": "Кур'єр CloudCommerce"
              },
              {
                "p_id": "6",
                "p_name": "Міст Експрес"
              },
              {
                "p_id": "7",
                "p_name": "MyMeest"
              },
              {
                "p_id": "8",
                "p_name": "Meest International"
              }
            ]
          },
          "status": {
            "code": "ok"
          }
        }

    :>json integer p_id: код типа доставки
    :>json string p_name: наименование типа доставки


PackTypeList
-----------------

Метод используется для получения перечня типов упаковочных материалов.


.. http:get:: https://api.cloudcommerce.zd.ua/wms/v1/PackTypeList?APIKEY=(int:APIKEY)


    **Example request**:

    .. tabs::

        .. code-tab:: bash

            $ curl https://api.cloudcommerce.zd.ua/wms/v1/PackTypeList?APIKEY=83F5428CBAE296FFE0509CB9CB2A24EB

        .. code-tab:: python

            import requests
            URL = 'https://api.cloudcommerce.zd.ua/wms/v1/PackTypeList?APIKEY=83F5428CBAE296FFE0509CB9CB2A24EB'
            response = requests.get(URL)
            print(response.json())

    **Example response**:

    .. sourcecode:: json

        {
          "response": {
            "packtype": [
              {
                "p_id": "1",
                "p_name": "Закрытый"
              },
              {
                "p_id": "2",
                "p_name": "Экран"
              },
              {
                "p_id": "3",
                "p_name": "Поддон"
              },
              {
                "p_id": "4",
                "p_name": "Гофро Пошта"
              }
            ]
          },
          "status": {
            "code": "ok"
          }
        }

    :>json integer p_id: код типа упаковки
    :>json string p_name: наименование типа упаковки


GoodsGroupsList
-----------------

Метод используется для получения перечня используемых групп из справочника “Группы товара”.


.. http:get:: https://api.cloudcommerce.zd.ua/wms/v1/GoodsGroupsList?APIKEY=(int:APIKEY)


    **Example request**:

    .. tabs::

        .. code-tab:: bash

            $ curl https://api.cloudcommerce.zd.ua/wms/v1/GoodsGroupsList?APIKEY=83F5428CBAE296FFE0509CB9CB2A24EB

        .. code-tab:: python

            import requests
            URL = 'https://api.cloudcommerce.zd.ua/wms/v1/GoodsGroupsList?APIKEY=83F5428CBAE296FFE0509CB9CB2A24EB'
            response = requests.get(URL)
            print(response.json())

    **Example response**:

    .. sourcecode:: json

        {
          "response": {
            "goods_groups": [
              {
                "p_id": "1001003",
                "p_name": "Одежда",
                "p_ext_sys_guid": null
              },
              {
                "p_id": "1008648",
                "p_name": "Обувь",
                "p_ext_sys_guid": null
              }
            ]
          },
          "status": {
            "code": "ok"
          }
        }

    :>json integer p_id: внутренний идентификатор группы товаров
    :>json string p_name: наименование группы товаров
    :>json string p_ext_sys_guid: внешний идентификатор группы товаров


MeasurementUnitList
---------------------

Метод используется для получения информации из справочника “Единицы измерения”.


.. http:get:: https://api.cloudcommerce.zd.ua/wms/v1/MeasurementUnitList?APIKEY=(int:APIKEY)


    **Example request**:

    .. tabs::

        .. code-tab:: bash

            $ curl https://api.cloudcommerce.zd.ua/wms/v1/MeasurementUnitList?APIKEY=83F5428CBAE296FFE0509CB9CB2A24EB

        .. code-tab:: python

            import requests
            URL = 'https://api.cloudcommerce.zd.ua/wms/v1/MeasurementUnitList?APIKEY=83F5428CBAE296FFE0509CB9CB2A24EB'
            response = requests.get(URL)
            print(response.json())

    **Example response**:

    .. sourcecode:: json

        {
          "response": {
            "measurement_unit": [
              {
                "p_id": "1",
                "p_name": "шт",
                "p_full_name": "Штука",
                "p_cod_kspovo": "2009"
              },
              {
                "p_id": "2",
                "p_name": "кг",
                "p_full_name": "Килограмм",
                "p_cod_kspovo": "0301"
              },
              {
                "p_id": "3",
                "p_name": "пара",
                "p_full_name": "Пара",
                "p_cod_kspovo": "1617"
              },
              {
                "p_id": "4",
                "p_name": "парт",
                "p_full_name": "Партия",
                "p_cod_kspovo": "2006"
              },
              {
                "p_id": "5",
                "p_name": "кор",
                "p_full_name": "Коробка",
                "p_cod_kspovo": "2052"
              },
              {
                "p_id": "6",
                "p_name": "бут",
                "p_full_name": "Бутылка",
                "p_cod_kspovo": "2061"
              },
              {
                "p_id": "7",
                "p_name": "упак",
                "p_full_name": "Упаковка",
                "p_cod_kspovo": "2110"
              },
              {
                "p_id": "8",
                "p_name": "пач",
                "p_full_name": "Пачка",
                "p_cod_kspovo": "2112"
              },
              {
                "p_id": "9",
                "p_name": "100 шт",
                "p_full_name": "Сто штук",
                "p_cod_kspovo": "2012"
              },
              {
                "p_id": "10",
                "p_name": "л",
                "p_full_name": "Литр",
                "p_cod_kspovo": "0138"
              },
              {
                "p_id": "11",
                "p_name": "м",
                "p_full_name": "Метр",
                "p_cod_kspovo": "0101"
              },
              {
                "p_id": "12",
                "p_name": "меш",
                "p_full_name": "Мешок",
                "p_cod_kspovo": "2060"
              },
              {
                "p_id": "13",
                "p_name": "рул",
                "p_full_name": "Рулон",
                "p_cod_kspovo": "2116"
              },
              {
                "p_id": "14",
                "p_name": "ящ",
                "p_full_name": "Ящик",
                "p_cod_kspovo": "2075"
              },
              {
                "p_id": "15",
                "p_name": "г",
                "p_full_name": "Грамм",
                "p_cod_kspovo": "0303"
              },
              {
                "p_id": "16",
                "p_name": "компл",
                "p_full_name": "Комплект",
                "p_cod_kspovo": "0671"
              }
            ]
          },
          "status": {
            "code": "ok"
          }
        }

    :>json integer p_id: идентификатор единицы измерения
    :>json string p_name: наименование единицы измерения
    :>json string p_full_name: полное название единицы измерения
    :>json string p_cod_kspovo: код по классификатору КСПОВО


TZoneList
---------------------

Метод используется для получения информации из справочника “Температурные зоны”.


.. http:get:: https://api.cloudcommerce.zd.ua/wms/v1/TZoneList?APIKEY=(int:APIKEY)


    **Example request**:

    .. tabs::

        .. code-tab:: bash

            $ curl https://api.cloudcommerce.zd.ua/wms/v1/TZoneList?APIKEY=83F5428CBAE296FFE0509CB9CB2A24EB

        .. code-tab:: python

            import requests
            URL = 'https://api.cloudcommerce.zd.ua/wms/v1/TZoneList?APIKEY=83F5428CBAE296FFE0509CB9CB2A24EB'
            response = requests.get(URL)
            print(response.json())

    **Example response**:

    .. sourcecode:: json

        {
          "response": {
            "tzone": [
              {
                "p_id": "1",
                "p_name": "Тепла"
              },
              {
                "p_id": "2",
                "p_name": "Холодна"
              }
            ]
          },
          "status": {
            "code": "ok"
          }
        }

    :>json integer p_id:  идентификатор температурной зоны
    :>json string p_name: название температурной зоны


WarehouseList
---------------------

Данный метод используется для получения кодов и наименований складов из справочника “Склады”, доступных к размещению товаров.


.. http:get:: https://api.cloudcommerce.zd.ua/wms/v1/WarehouseList?APIKEY=(int:APIKEY)


    **Example request**:

    .. tabs::

        .. code-tab:: bash

            $ curl https://api.cloudcommerce.zd.ua/wms/v1/WarehouseList?APIKEY=83F5428CBAE296FFE0509CB9CB2A24EB

        .. code-tab:: python

            import requests
            URL = 'https://api.cloudcommerce.zd.ua/wms/v1/WarehouseList?APIKEY=83F5428CBAE296FFE0509CB9CB2A24EB'
            response = requests.get(URL)
            print(response.json())

    **Example response**:

    .. sourcecode:: json

        {
          "response": {
            "warehouse": [
              {
                "p_id": "5",
                "p_name": "Istanbul, 3. Cd. No:8, Beylikdüzü, Turkey"
              },
              {
                "p_id": "4",
                "p_name": "Вишневое, Промышленная, 10"
              },
              {
                "p_id": "2",
                "p_name": "Склад TEST"
              }
            ]
          },
          "status": {
            "code": "ok"
          }
        }

    :>json integer p_id: идентификатор склада
    :>json string p_name: наименование склада
