Товари и остатки
==================

Товары считываются через GoodsList, обновляються через GoodsModify,
GoodsMUnitModify, GoodsBarcodeModify, GoodsBatchModify.

Остатки по товарам можно получить через GoodsStock


GoodsList
---------------------

Метод используется для получения списка товаров со стандартными
характеристиками из справочника “Товары”, а так же получения информации
о товаре по его внутреннему (ID), внешнему (EXTGUID) номеру или артикулу (SKU)


.. http:get:: https://api.cloudcommerce.zd.ua/wms/v1/GoodsList?APIKEY=(str:APIKEY)&ID=(str:ID)&EXTGUID=(str:EXTGUID)


    **Example request**:

    .. tabs::

        .. code-tab:: bash

            $ curl https://api.cloudcommerce.zd.ua/wms/v1/GoodsList?APIKEY=83F5428CBAE296FFE0509CB9CB2A24EB

        .. code-tab:: python

            import requests
            URL = 'https://api.cloudcommerce.zd.ua/wms/v1/GoodsList?APIKEY=83F5428CBAE296FFE0509CB9CB2A24EB'
            response = requests.get(URL)
            print(response.json())

    **Example response**:

    .. sourcecode:: json

        {
          "response": {
            "goods": [
              {
                "p_id": "1092931",
                "p_sku": "23234234234234207",
                "p_name": "description: Товар 5, client_id: 144994.0, 2, [Children’s shoes, price: 8.0, quantity: 2],[Children’s shoes, price: 7.35, quantity: 3]",
                "p_gg_id": null,
                "p_storage_model": "1",
                "p_photo_link": null,
                "p_experation_day": null,
                "p_tzone_id": null,
                "p_ext_sys_guid": "85beb7f3-c6e7-4f10-86dd-170d42006c72",
                "goods_props": [
                  {
                    "p_name": "ЦВЕТ",
                    "p_value": "Белый"
                  }
                ],
                "goods_munit": [
                  {
                    "p_id": "1092932",
                    "p_ext_sys_guid": "85beb7f3-c6e7-4f10-86dd-170d42006c72",
                    "p_mu_id": "1",
                    "p_pack_id": null,
                    "p_name": "шт",
                    "p_k": "1",
                    "p_base_unit": "1",
                    "p_qty_in_layer": null,
                    "p_layers_on_pallet": null,
                    "p_weight": "1.1",
                    "p_length": null,
                    "p_width": null,
                    "p_height": null,
                    "goods_munit_props": [
                      {
                        "p_name": "ЦВЕТ",
                        "p_value": "Белый"
                      }
                    ],
                ],
                "goods_barcode": [
                  {
                    "p_id": "1092933",
                    "p_goods_munit_id": "1092932",
                    "p_goods_batch_id": null,
                    "p_sn_flag": "0",
                    "p_barcode": "23234234234234207",
                    "p_barcode_synonym": null,
                    "p_note": null,
                    "p_ext_sys_guid": "85beb7f3-c6e7-4f10-86dd-170d42006c72"
                  }
                ],
                "goods_batch": [
                  {
                    "p_id": "1092933",
                    "p_goods_munit_id": "1092932",
                    "p_goods_batch_id": null,
                    "p_sn_flag": "0",
                    "p_barcode": "23234234234234207",
                    "p_barcode_synonym": null,
                    "p_note": null,
                    "p_ext_sys_guid": "85beb7f3-c6e7-4f10-86dd-170d42006c72"
                  }
                ]
              }
            ]
          },
          "status": {
            "code": "ok",
            "message": ""
          }
        }

    :query string ID: внутренний код товара
    :query string EXTGUID: внешний код товара
    :query string SKU: артикул товара
    :>json integer p_id: внутренний идентификатор товара
    :>json string p_name: наименование товара
    :>json string p_sku: артикул товара
    :>json integer p_gg_id: внутренний идентификатор группы товаров (метод для получения значений GoodsGroupsList)
    :>json integer p_storage_model:  модель учета (1 - без деления, 2 - по партиям, 3 - по серийным номерам)
    :>json string p_photo_link: ссылка на фото
    :>json integer p_experation_day: срок реализации в днях (количество дней с даты  производства до окончания срока годности)
    :>json integer p_tzone_id: код температурной зоны (метод для получения значений TZoneList)
    :>json string p_ext_sys_guid: внешний идентификатор товара
    :>json list goods_props: дополнительные свойства товара
    :>json string p_name: наименование свойства
    :>json string p_value: значение свойства
    :>json list goods_munit: основные свойства товара
    :>json integer p_id: внутренний код единицы измерения
    :>json string p_name: название единицы измерения
    :>json string p_ext_sys_guid: внешний код единицы измерения
    :>json string p_mu_id: внутренний код справочника единиц измерения (метод для получения справочника MeasurementUnitList)
    :>json integer p_pack_id: внутренний код упаковки (метод для получения справочника PackagingList)
    :>json float p_k: коэффициент пересчета к базовой единице измерения
    :>json integer p_base_unit: признак базовой единицы измерения (0-нет, 1-да)
    :>json integer p_qty_in_layer: количество (в указанной единице измерения) в слое на паллете
    :>json integer p_layers_on_pallet: количество слоев на паллете
    :>json float p_weight:  вес товара в указанной единице измерения
    :>json float p_length: длина товара в указанной единице измерения
    :>json float p_width: ширина товара в указанной единице измерения
    :>json float p_height: высота товара в указанной единице измерения
    :>json integer p_is_active: активность единицы измерения (0 – не активна; 1 – активна)
    :>json list goods_batch: партия товара
    :>json integer p_id: внутренний идентификатор партии товара
    :>json string p_name: наименование партии товара
    :>json string p_ext_sys_guid: внешний идентификатор партии товара
    :>json string p_manufacturing_date: дата производства
    :>json string p_expiration_date: дата окончания срока годности
    :>json string p_part_number: номер партии
    :>json string p_haccp: HACCP
    :>json list goods_barcode: партия товара
    :>json integer p_id: внутренний идентификатор штрих кода
    :>json string p_barcode: штрих код товара
    :>json string p_barcode_synonym:  штрих код синоним
    :>json integer p_goods_munit_id: внутренний идентификатор единицы измерения (метод для получения справочника GoodsMUnitModify)
    :>json integer p_goods_batch_id: внутренний идентификатор партии (метод для получения GoodsBatchModify)
    :>json integer p_sn_flag: признак, что штрих код - это серийный номер (используется в модели учета товара по серийным номерам, параметр "storage_model": 3)
    :>json string p_note: примечание
    :>json string ext_sys_guid: внешний идентификатор штрих кода



GoodsModify
---------------------

Метод используется для создания/редактирования карточки товара в справочнике “Товары”.


.. http:post:: https://api.cloudcommerce.zd.ua/wms/v1/GoodsModify


    **Example request**:

    .. tabs::

        .. code-tab:: bash

            $ curl \
                -X POST \
                -H "Content-Type: application/json" \
                -d @body.json \
                https://api.cloudcommerce.zd.ua/wms/v1/GoodsModify

        .. code-tab:: python

            import requests
            import json
            URL = 'https://api.cloudcommerce.zd.ua/wms/v1/GoodsModify'
            data = json.load(open('body.json', 'rb'))
            response = requests.post(URL, json=data)
            print(response.json())

    The content of body.json is like:

    .. code-block:: json

        {
          "p_api_key": "83F5428CBAE296FFE0509CB9CB2A24EB",
          "p_id": null,
          "p_sku": "0023",
          "p_name": "Спец товар СП-01",
          "p_gg_id": null,
          "p_sm": 2,
          "p_days": 90,
          "p_link": "",
          "p_tzone_id": null,
          "p_ext_sys_guid": "0023-23",
          "p_gg_ext_sys_guid": null,
          "p_ask_part_number": 0,
          "p_batch_date_type": 0,
          "p_goods_type": 1,
          "p_is_large_home_device": 2,
          "p_props": [
            {
              "name": "Цвет",
              "value": "Белый"
            }
          ],
          "p_base_munit": {
            "p_ext_sys_guid": "5625486",
            "p_mu_id": 1,
            "p_cod_kspovo": "2009",
            "p_pack_id": null,
            "p_pack_ext_sys_guid": null,
            "p_qty_in_layer": 2,
            "p_layers_on_pallet": 1,
            "p_weight": 30,
            "p_length": 500,
            "p_width": 600,
            "p_height": 500,
            "p_is_active": 1,
            "p_props": [
              {
                "name": "Цвет",
                "value": "Белый"
              }
            ]
          },
          "p_abc_group": null,
          "p_picking_qty_min": 10,
          "p_manufacturing_date_more": 2,
          "p_manufacturing_date_last": 7
        }


GoodsMUnitModify
---------------------

Метод используется для создания/редактирования единиц измерения конкретного товара в справочнике “Товары”.


.. http:post:: https://api.cloudcommerce.zd.ua/wms/v1/GoodsMUnitModify


    **Example request**:

    .. tabs::

        .. code-tab:: bash

            $ curl \
                -X POST \
                -H "Content-Type: application/json" \
                -d @body.json \
                https://api.cloudcommerce.zd.ua/wms/v1/GoodsMUnitModify

        .. code-tab:: python

            import requests
            import json
            URL = 'https://api.cloudcommerce.zd.ua/wms/v1/GoodsMUnitModify'
            data = json.load(open('body.json', 'rb'))
            response = requests.post(URL, json=data)
            print(response.json())

    The content of body.json is like:

    .. code-block:: json

        {
          "p_api_key": "83F5428CBAE296FFE0509CB9CB2A24EB",
          "p_goods_id": 1010862,
          "p_ext_sys_guid": "64351564845",
          "p_goods_ext_sys_guid": "",
          "p_mu_id": 1,
          "p_cod_kspovo": "2009",
          "p_pack_id": null,
          "p_pack_ext_sys_guid": null,
          "p_k": 12,
          "p_base_unit": 0,
          "p_qty_in_layer": 100,
          "p_layers_on_pallet": 5,
          "p_weight": 0.5,
          "p_length": 50,
          "p_width": 50,
          "p_height": 200,
          "p_is_active": 1,
          "p_props": [
            {
              "name": "Объем основной",
              "value": "0,45"
            }
          ]
        }


GoodsBarcodeModify
---------------------

Данный метод используется для создания/редактирования штрих кода конкретного товара и его единицы измерения в справочнике “Товары”.


.. http:post:: https://api.cloudcommerce.zd.ua/wms/v1/GoodsBarcodeModify


    **Example request**:

    .. tabs::

        .. code-tab:: bash

            $ curl \
                -X POST \
                -H "Content-Type: application/json" \
                -d @body.json \
                https://api.cloudcommerce.zd.ua/wms/v1/GoodsBarcodeModify

        .. code-tab:: python

            import requests
            import json
            URL = 'https://api.cloudcommerce.zd.ua/wms/v1/GoodsBarcodeModify'
            data = json.load(open('body.json', 'rb'))
            response = requests.post(URL, json=data)
            print(response.json())

    The content of body.json is like:

    .. code-block:: json

        {
          "p_api_key": "83F5428CBAE296FFE0509CB9CB2A24EB",
          "p_id": null,
          "p_ext_sys_guid": null,
          "p_goods_id": 1010862,
          "p_goods_ext_sys_guid": "",
          "p_goods_munit_id": 1010864,
          "p_goods_munit_esg": "",
          "p_goods_batch_id": null,
          "p_goods_batch_esg": null,
          "p_note": null,
          "p_sn_flag": 0,
          "p_barcode": "4820042653343"
        }


GoodsBatchModify
---------------------

Метод используется для создания и редактирования партий товара.


.. http:post:: https://api.cloudcommerce.zd.ua/wms/v1/GoodsBarcodeModify


    **Example request**:

    .. tabs::

        .. code-tab:: bash

            $ curl \
                -X POST \
                -H "Content-Type: application/json" \
                -d @body.json \
                https://api.cloudcommerce.zd.ua/wms/v1/GoodsBarcodeModify

        .. code-tab:: python

            import requests
            import json
            URL = 'https://api.cloudcommerce.zd.ua/wms/v1/GoodsBarcodeModify'
            data = json.load(open('body.json', 'rb'))
            response = requests.post(URL, json=data)
            print(response.json())

    The content of body.json is like:

    .. code-block:: json

        {
          "p_api_key": "83F5428CBAE296FFE0509CB9CB2A24EB",
          "p_id": null,
          "p_ext_sys_guid": null,
          "p_goods_id": 1010862,
          "p_goods_ext_sys_guid": null,
          "p_manufacturing_date": "21.04.2018",
          "p_expiration_date": "11.05.2018",
          "p_part_number": null,
          "p_haccp": null
        }


GoodsStock
---------------------

Метод позволяет получить отчет по текущим остаткам товаров.


.. http:get:: https://api.cloudcommerce.zd.ua/wms/v1/GoodsStock?APIKEY=(str:APIKEY)&ID=(str:ID)&EXTGUID=(str:EXTGUID)


    **Example request**:

    .. tabs::

        .. code-tab:: bash

            $ curl https://api.cloudcommerce.zd.ua/wms/v1/GoodsStock?APIKEY=83F5428CBAE296FFE0509CB9CB2A24EB

        .. code-tab:: python

            import requests
            URL = 'https://api.cloudcommerce.zd.ua/wms/v1/GoodsStock?APIKEY=83F5428CBAE296FFE0509CB9CB2A24EB'
            response = requests.get(URL)
            print(response.json())

    **Example response**:

    .. sourcecode:: json

        {
          "response": {
            "goods_stock": [
              {
                "p_goods_id": 1003828,
                "p_goods_sku": "1009-50201-12743/3111/30:34",
                "p_goods_name": "1009-50201-12743/3111/30:34",
                "p_goods_ext_sys_guid": null,
                "p_goods_munit_id": 1004774,
                "p_goods_munit_name": "шт",
                "p_goods_munit_ext_sys_guid": null,
                "p_goods_batch_id": null,
                "p_goods_batch_name": null,
                "p_goods_barcode_id": 1006114,
                "p_goods_barcode_name": "8680890342644",
                "p_quality": 1,
                "p_quality_name": "Кондиция",
                "p_qty": 1,
                "p_manufacturer_id": null,
                "p_manufacturer_esg": null
              }
            ]
          },
          "status": {
            "code": "ok",
            "message": ""
          }
        }

    :query string ID: внутренний код товара
    :query string EXTGUID: внешний код товара
    :>json integer p_goods_id: внутренний идентификатор товара
    :>json string p_goods_sku: наименование товара
    :>json string p_goods_name: артикул товара
    :>json string p_goods_ext_sys_guid: внешний идентификатор товара
    :>json integer p_goods_munit_id: внутренний идентификатор единицы измерения (метод для получения справочника MeasurementUnitList)
    :>json string p_goods_munit_name: название единицы измерения товара
    :>json string p_goods_munit_ext_sys_guid: внешний идентификатор единицы измерения товара
    :>json integer p_goods_batch_id: внутренний идентификатор партии
    :>json string p_goods_batch_name: название партии
    :>json integer p_goods_barcode_id: внутренний идентификатор штрих кода товара
    :>json string p_goods_barcode_name: название штрих кода товара
    :>json integer p_quality: внутренний идентификатор качества
    :>json string p_quality_name: название качества
    :>json float p_qty: количество товара
    :>json integer p_manufacturer_id: внутренний идентификатор производителя
    :>json string p_manufacturer_esg: внешний идентификатор производителя



