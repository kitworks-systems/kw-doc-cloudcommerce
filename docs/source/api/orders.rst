Заказы
==================



OrdersList
---------------------

Метод используется для получения списка заказов за выбранный период со
статусами выполнения, а также отдельного заказа в системе по
внутреннему ID или внешнему EXTGUID идентификатору.


.. http:get:: https://api.cloudcommerce.zd.ua/wms/v1/GoodsList?APIKEY=(str:APIKEY)&ID=(str:ID)&EXTGUID=(str:EXTGUID)
&DATE_FROM={{string}}&DATE_TO={{string}}&ORDER_FILES={{number}}&ORDER_LOG={{number}}&DOC_STATUS_ID={{number}}

    **Example request**:

    .. tabs::

        .. code-tab:: bash

            $ curl https://api.cloudcommerce.zd.ua/wms/v1/OrdersList?APIKEY=83F5428CBAE296FFE0509CB9CB2A24EB

        .. code-tab:: python

            import requests
            URL = 'https://api.cloudcommerce.zd.ua/wms/v1/OrdersList?APIKEY=83F5428CBAE296FFE0509CB9CB2A24EB'
            response = requests.get(URL)
            print(response.json())

    :query string ID: внутренний код товара
    :query string EXTGUID: внешний код товара
    :query string DATE_FROM: внешний код товара
    :query string DATE_TO: внешний код товара
    :query string ORDER_FILES: внешний код товара
    :query string ORDER_LOG: внешний код товара
    :query string DOC_STATUS_ID: внешний код товара

    **Example response**:

    .. sourcecode:: json

        {
          "response": {
            "orders": [
              {
                "p_id": "10111736",
                "p_doc_date": "21-NOV-21",
                "p_doc_status_id": "14",
                "p_doc_status_name": "Отменен",
                "p_operation_type_id": "5",
                "p_operation_type_name": "Заказ B2B",
                "p_wh_id": "2",
                "p_shipment_plan_date": "21-NOV-21",
                "p_delivery_type_id": "1",
                "p_delivery_type_name": "Самовивіз",
                "p_contragent_name": "Тест",
                "p_contragent_telnum": "0671234567",
                "p_ext_sys_docnum": null,
                "p_ext_sys_guid": null,
                "p_comments": null,
                "p_delivery_address": null,
                "p_waybill": null,
                "p_decl_request": null,
                "p_decl_response": null,
                "p_decl_uuid": null,
                "p_comments_pack": null,
                "orders_items": [
                  {
                    "p_id": "2379800",
                    "p_goods_id": "1076281",
                    "p_goods_munit_id": "1076282",
                    "p_goods_quality_id": "1",
                    "p_goods_barcode_id": null,
                    "p_qty": "5",
                    "p_serialnumber": null,
                    "p_manufacturing_date_min": null,
                    "p_manufacturing_date_max": null,
                    "p_expiration_date_min": null,
                    "p_expiration_date_max": null,
                    "p_part_number": null,
                    "p_price": null,
                    "p_total_price": null,
                    "p_goods_ext_sys_guid": null,
                    "p_goods_munit_ext_sys_guid": null
                  }
                ],
                "orders_seats": []
              },
            ]
          },
          "status": {
            "code": "ok",
            "message": ""
          }
        }

    :>json integer p_id: внутренний идентификатор заказа
    :>json string p_doc_date: дата заказа
    :>json integer p_doc_status_id: внутренний идентификатор статуса документа
    :>json string p_doc_status_name: название статуса документа
    :>json integer p_operation_type_id: внутренний идентификатор типа заказа
    :>json string p_operation_type_name: название типа заказа
    :>json integer p_wh_id: внутренний идентификатор склада (метод для получения справочника WarehouseList)
    :>json date p_shipment_plan_date: плановая дата отгрузки
    :>json integer p_delivery_type_id: код типа доставки
    :>json string p_delivery_type_name: название типа доставки
    :>json string p_contragent_name: контрагент/Получатель (наименование)
    :>json string p_contragent_telnum: контрагент/Получатель (телефон)
    :>json string p_ext_sys_docnum: внешний номер заказа
    :>json string p_ext_sys_guid: внешний идентификатор заказа
    :>json string p_comments: комментарий
    :>json string p_delivery_address: адрес доставки
    :>json string p_waybill: признак, объединяющий заказы для отгрузки (накладная, путевой лист, водитель, автомобиль)
    :>json integer p_load_order: порядок загрузки
    :>json string p_decl_request: запрос к перевозчику на регистрацию посылки
    :>json string p_decl_response: ответ от перевозчика на регистрацию посылки
    :>json string p_decl_uuid:  уникальный код посылки у перевозчика
    :>json string p_decl_number: номер документа перевозчика
    :>json string p_comments_pack: комментарий к упаковке


