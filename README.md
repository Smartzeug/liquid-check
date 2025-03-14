# 🚰Liquid Check🚰

Codeschnipsel aus diesem Video https://www.youtube.com/watch?v=aPMkGitji_Q&t=2129s
![Screenshot 13 03 2025 um 22 12 33 PM](https://github.com/user-attachments/assets/e180d68a-5b78-403e-9f55-6b8b539e4897)
![Screenshot 13 03 2025 um 22 14 56 PM](https://github.com/user-attachments/assets/abf386e4-0300-4e53-a849-cee1d0b9766d)


```
rest:
    scan_interval: 60
    resource: http://IPLIQUIDCHECK/infos.json
    sensor:
      - name: Zisterne Füllstand in Meter
        value_template: "{{ value_json.payload.measure.level }}"
        unit_of_measurement: Meter
      - name: Zisterne Inhalt in Liter
        value_template: "{{ value_json.payload.measure.content }}"
        unit_of_measurement: Liter
```

```
rest_command:
  messung_zisterne:
    url: http://IPLIQUIDCHECK/command
    method: POST
    payload: '{ "header" : { "namespace" : "Device.Control" , "name" : "StartMeasure" , "messageId" : "1" , "payloadVersion" : "1" } , "payload" : null }' 
    content_type: 'application/json; charset=utf-8'
```


