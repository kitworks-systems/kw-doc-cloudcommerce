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
                    "p_height": null
                  }
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
                "goods_batch": []
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

