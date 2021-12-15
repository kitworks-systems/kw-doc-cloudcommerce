Справочники
=============


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

    :>json string p_id: код группы качества
    :>json integer p_name: наименование группы качества
    :>json string p_stype: тип качества

