# io7_chap11

![IMG_1588](https://github.com/user-attachments/assets/5dcaab19-57ca-4136-a1c9-c3fe57726195)


[flows (3).json](https://github.com/user-attachments/files/23607155/flows.3.json)
[
    {
        "id": "19ce8e091ec31145",
        "type": "tab",
        "label": "Flow 1",
        "disabled": false,
        "info": "",
        "env": []
    },
    {
        "id": "b6b83a14f63600be",
        "type": "group",
        "z": "19ce8e091ec31145",
        "name": "Thermostat and Valve",
        "style": {
            "label": true,
            "color": "#001f60",
            "stroke": "#ffcf3f"
        },
        "nodes": [
            "ae5554a075d84e77",
            "2ff3c5440a7b77e8",
            "74bbfa8084ee2142",
            "68a64476460c7d6f",
            "57d3ed23a82592fb",
            "1a3230551bf76c04",
            "461cf2b639d4583e",
            "f3911989ab46b393",
            "e18167ea5ca728f0",
            "351e965eb6f7afa1",
            "2ddc984986c8d1c5",
            "f82378ab33e2a324",
            "caf7860765c0401f",
            "aa2e8e64bb85941f"
        ],
        "x": 34,
        "y": 139,
        "w": 872,
        "h": 262
    },
    {
        "id": "d8fd34e3306fa741",
        "type": "group",
        "z": "19ce8e091ec31145",
        "name": "Shadow Accessing",
        "style": {
            "label": true,
            "fill": "#ffefbf",
            "stroke": "#ffbfbf",
            "color": "#3f3f3f"
        },
        "nodes": [
            "0db4e79b55cfa7e0",
            "93b1bb0425f2d229",
            "78beeca7f28e0a11"
        ],
        "x": 34,
        "y": 419,
        "w": 672,
        "h": 142
    },
    {
        "id": "02205f7eef6c2ea7",
        "type": "group",
        "z": "19ce8e091ec31145",
        "name": "Shadow Query Example",
        "style": {
            "stroke": "#92d04f",
            "fill": "#e3f3d3",
            "label": true,
            "color": "#000000"
        },
        "nodes": [
            "020d332909f4e2ef",
            "5606930e6f071cb8",
            "4cd7d094ab316760",
            "c741bbd1b3aca8c4",
            "0596e3f2e8c9c4d6",
            "89418712b3a4e644",
            "9ecd979073771698",
            "3435ab72215017d8"
        ],
        "x": 34,
        "y": 579,
        "w": 692,
        "h": 242
    },
    {
        "id": "ae5554a075d84e77",
        "type": "io7 in",
        "z": "19ce8e091ec31145",
        "g": "b6b83a14f63600be",
        "name": "",
        "deviceId": "valve1",
        "authentication": "a7a1ab528ff10487",
        "evt": "status",
        "fmt": "json",
        "qos": "0",
        "allDevices": false,
        "allEvents": false,
        "allFormats": false,
        "x": 110,
        "y": 180,
        "wires": [
            [
                "57d3ed23a82592fb"
            ]
        ]
    },
    {
        "id": "2ff3c5440a7b77e8",
        "type": "io7 out",
        "z": "19ce8e091ec31145",
        "g": "b6b83a14f63600be",
        "authentication": "a7a1ab528ff10487",
        "name": "",
        "deviceId": "valve1",
        "cmd": "power",
        "fmt": "json",
        "qos": "0",
        "retain": "false",
        "x": 830,
        "y": 180,
        "wires": []
    },
    {
        "id": "74bbfa8084ee2142",
        "type": "io7 out",
        "z": "19ce8e091ec31145",
        "g": "b6b83a14f63600be",
        "authentication": "a7a1ab528ff10487",
        "name": "",
        "deviceId": "rotary1",
        "cmd": "set",
        "fmt": "json",
        "qos": "0",
        "retain": "false",
        "x": 820,
        "y": 360,
        "wires": []
    },
    {
        "id": "68a64476460c7d6f",
        "type": "io7 in",
        "z": "19ce8e091ec31145",
        "g": "b6b83a14f63600be",
        "name": "",
        "deviceId": "rotary1",
        "authentication": "a7a1ab528ff10487",
        "evt": "status",
        "fmt": "json",
        "qos": "0",
        "allDevices": false,
        "allEvents": false,
        "allFormats": false,
        "x": 110,
        "y": 360,
        "wires": [
            [
                "f3911989ab46b393"
            ]
        ]
    },
    {
        "id": "57d3ed23a82592fb",
        "type": "function",
        "z": "19ce8e091ec31145",
        "g": "b6b83a14f63600be",
        "name": "update ui",
        "func": "msg.payload = msg.payload.d.valve;\nreturn msg;",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 300,
        "y": 180,
        "wires": [
            [
                "f82378ab33e2a324"
            ]
        ]
    },
    {
        "id": "1a3230551bf76c04",
        "type": "function",
        "z": "19ce8e091ec31145",
        "g": "b6b83a14f63600be",
        "name": "command",
        "func": "msg.payload = {\n    \"d\" : {\n        \"valve\" : msg.payload\n    }\n}\nreturn msg;\n",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 660,
        "y": 180,
        "wires": [
            [
                "2ff3c5440a7b77e8"
            ]
        ]
    },
    {
        "id": "461cf2b639d4583e",
        "type": "function",
        "z": "19ce8e091ec31145",
        "g": "b6b83a14f63600be",
        "name": "automate",
        "func": "const client = global.get('redisClient');\n\n// thermometer1 shadow 읽기\nlet thermo = await client.jget(\"thermometer1\");\nlet temperature = thermo?.temperature ?? 20;\n\n// rotary1 shadow 읽기\nlet rotary = await client.jget(\"rotary1\");\n\n// Lab3에서 요구하는 ‘target’\nlet target = rotary?.target ?? rotary?.value ?? 15;\n\n// 자동제어 로직\nlet evt = { d: {} };\n\nif (target > temperature) {\n    evt.d.valve = \"on\";\n} else {\n    evt.d.valve = \"off\";\n}\n\nreturn { payload: evt };\n",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 660,
        "y": 260,
        "wires": [
            [
                "2ff3c5440a7b77e8"
            ]
        ]
    },
    {
        "id": "f3911989ab46b393",
        "type": "function",
        "z": "19ce8e091ec31145",
        "g": "b6b83a14f63600be",
        "name": "update ui 3",
        "func": "const client = global.get(\"redisClient\");\n\n// 로터리 raw value (0~255)\nlet raw = msg.payload.d.value;\n\n// 0~60으로 변환\nlet target = Math.round(raw * 60 / 255);\n\n// Shadow 업데이트\nawait client.jset(\"rotary1\", { target: target });\n\n// UI로 보낼 payload 설정\nmsg.payload = target;\n\nreturn msg;\n",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 310,
        "y": 360,
        "wires": [
            [
                "461cf2b639d4583e",
                "aa2e8e64bb85941f"
            ]
        ]
    },
    {
        "id": "e18167ea5ca728f0",
        "type": "function",
        "z": "19ce8e091ec31145",
        "g": "b6b83a14f63600be",
        "name": "command",
        "func": "const map = (num, inMin, inMax, outMin, outMax) => {\n    return Math.round(((num - inMin) * (outMax - outMin)) / (inMax - inMin) + outMin);\n}\n\nmsg.payload = {\n    \"d\" : {\n        \"value\" : map(msg.payload, 10, 60, 0, 255)\n    }\n}\nreturn msg;\n",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 660,
        "y": 360,
        "wires": [
            [
                "74bbfa8084ee2142"
            ]
        ]
    },
    {
        "id": "351e965eb6f7afa1",
        "type": "io7 in",
        "z": "19ce8e091ec31145",
        "g": "b6b83a14f63600be",
        "name": "",
        "deviceId": "thermostat1",
        "authentication": "a7a1ab528ff10487",
        "evt": "status",
        "fmt": "json",
        "qos": "0",
        "allDevices": false,
        "allEvents": false,
        "allFormats": false,
        "x": 130,
        "y": 260,
        "wires": [
            [
                "2ddc984986c8d1c5"
            ]
        ]
    },
    {
        "id": "2ddc984986c8d1c5",
        "type": "function",
        "z": "19ce8e091ec31145",
        "g": "b6b83a14f63600be",
        "name": "update ui 2",
        "func": "msg.payload = msg.payload.d.temperature;\n\n\nreturn msg;",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 310,
        "y": 260,
        "wires": [
            [
                "caf7860765c0401f"
            ]
        ]
    },
    {
        "id": "f82378ab33e2a324",
        "type": "ui-switch",
        "z": "19ce8e091ec31145",
        "g": "b6b83a14f63600be",
        "name": "",
        "label": "난방밸브",
        "group": "d7383ea4332dbe4a",
        "order": 2,
        "width": "2",
        "height": "3",
        "passthru": false,
        "decouple": true,
        "topic": "topic",
        "topicType": "msg",
        "style": "",
        "className": "",
        "layout": "row-spread-swapped",
        "clickableArea": "switch",
        "onvalue": "on",
        "onvalueType": "str",
        "onicon": "",
        "oncolor": "",
        "offvalue": "off",
        "offvalueType": "str",
        "officon": "",
        "offcolor": "",
        "x": 480,
        "y": 180,
        "wires": [
            [
                "1a3230551bf76c04"
            ]
        ]
    },
    {
        "id": "aa2e8e64bb85941f",
        "type": "ui-slider",
        "z": "19ce8e091ec31145",
        "g": "b6b83a14f63600be",
        "group": "d7383ea4332dbe4a",
        "name": "",
        "label": "설정온도",
        "tooltip": "",
        "order": 3,
        "width": "4",
        "height": "1",
        "passthru": false,
        "outs": "end",
        "topic": "topic",
        "topicType": "msg",
        "thumbLabel": "true",
        "showTicks": "always",
        "min": "10",
        "max": "30",
        "step": 1,
        "className": "",
        "iconPrepend": "",
        "iconAppend": "",
        "color": "",
        "colorTrack": "",
        "colorThumb": "",
        "showTextField": false,
        "x": 480,
        "y": 360,
        "wires": [
            [
                "e18167ea5ca728f0"
            ]
        ]
    },
    {
        "id": "caf7860765c0401f",
        "type": "ui-gauge",
        "z": "19ce8e091ec31145",
        "g": "b6b83a14f63600be",
        "name": "",
        "group": "d7383ea4332dbe4a",
        "order": 1,
        "value": "payload",
        "valueType": "msg",
        "width": 2,
        "height": "3",
        "gtype": "gauge-34",
        "gstyle": "needle",
        "title": "현재온도",
        "alwaysShowTitle": false,
        "floatingTitlePosition": "top-left",
        "units": "℃",
        "icon": "",
        "prefix": "",
        "suffix": "",
        "segments": [
            {
                "from": "10",
                "color": "#5cd65c",
                "text": "",
                "textType": "label"
            },
            {
                "from": "23",
                "color": "#ff9300",
                "text": "",
                "textType": "label"
            },
            {
                "from": "30",
                "color": "#ea5353",
                "text": "",
                "textType": "label"
            }
        ],
        "min": "10",
        "max": "30",
        "sizeThickness": 16,
        "sizeGap": 4,
        "sizeKeyThickness": 8,
        "styleRounded": true,
        "styleGlow": false,
        "className": "",
        "x": 480,
        "y": 260,
        "wires": [
            [
                "461cf2b639d4583e"
            ]
        ]
    },
    {
        "id": "0db4e79b55cfa7e0",
        "type": "inject",
        "z": "19ce8e091ec31145",
        "g": "d8fd34e3306fa741",
        "name": "at boot",
        "props": [
            {
                "p": "payload"
            },
            {
                "p": "topic",
                "vt": "str"
            }
        ],
        "repeat": "",
        "crontab": "",
        "once": true,
        "onceDelay": 0.1,
        "topic": "",
        "payload": "",
        "payloadType": "date",
        "x": 160,
        "y": 520,
        "wires": [
            [
                "93b1bb0425f2d229"
            ]
        ]
    },
    {
        "id": "93b1bb0425f2d229",
        "type": "function",
        "z": "19ce8e091ec31145",
        "g": "d8fd34e3306fa741",
        "name": "Redis Init",
        "func": "const client = redis.createClient({ url: 'redis://redis:6379' });\n\nclient.jget = async k => {\n    let objState = JSON.parse(await client.get(k));\n    if (objState === null) return null;\n    if (objState.hasOwnProperty('d')) {\n        return objState;\n    } else {\n        return {\n            d: objState,\n            t: await client.get(k + ':time')\n        }\n    }\n}\n\nclient.connect();\nglobal.set('redisClient', client);",
        "outputs": 1,
        "timeout": "",
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [
            {
                "var": "redis",
                "module": "redis"
            }
        ],
        "x": 600,
        "y": 520,
        "wires": [
            []
        ]
    },
    {
        "id": "78beeca7f28e0a11",
        "type": "comment",
        "z": "19ce8e091ec31145",
        "g": "d8fd34e3306fa741",
        "name": "it defines & inits a shadow accessing function. The shadow is updated by the API Server.",
        "info": "# how to access\n```javascript\nconst client = global.get('redisClient');\nconst keys = await client.keys(msg.payload);\n```",
        "x": 370,
        "y": 460,
        "wires": []
    },
    {
        "id": "020d332909f4e2ef",
        "type": "function",
        "z": "19ce8e091ec31145",
        "g": "02205f7eef6c2ea7",
        "name": "query all",
        "func": "const client = global.get('redisClient');\nconst keys = await client.keys(msg.payload);\n\nlet result = [];\nfor (let k of keys) {\n    let obj = {};\n    obj[k] = await client.jget(k);;\n    result.push(obj);\n}\n\nmsg.payload = result;\nreturn msg;",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 360,
        "y": 700,
        "wires": [
            [
                "4cd7d094ab316760"
            ]
        ]
    },
    {
        "id": "5606930e6f071cb8",
        "type": "inject",
        "z": "19ce8e091ec31145",
        "g": "02205f7eef6c2ea7",
        "name": "",
        "props": [
            {
                "p": "payload"
            },
            {
                "p": "topic",
                "vt": "str"
            }
        ],
        "repeat": "",
        "crontab": "",
        "once": false,
        "onceDelay": 0.1,
        "topic": "",
        "payload": "*",
        "payloadType": "str",
        "x": 130,
        "y": 680,
        "wires": [
            [
                "020d332909f4e2ef"
            ]
        ]
    },
    {
        "id": "4cd7d094ab316760",
        "type": "debug",
        "z": "19ce8e091ec31145",
        "g": "02205f7eef6c2ea7",
        "name": "debug 2",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "false",
        "statusVal": "",
        "statusType": "auto",
        "x": 600,
        "y": 700,
        "wires": []
    },
    {
        "id": "c741bbd1b3aca8c4",
        "type": "comment",
        "z": "19ce8e091ec31145",
        "g": "02205f7eef6c2ea7",
        "name": "This shows how to access the event shadow. Edit the Input node with the device id to query",
        "info": "",
        "x": 380,
        "y": 620,
        "wires": []
    },
    {
        "id": "0596e3f2e8c9c4d6",
        "type": "function",
        "z": "19ce8e091ec31145",
        "g": "02205f7eef6c2ea7",
        "name": "a device",
        "func": "const client = global.get('redisClient');\nmsg.payload = await client.jget(msg.payload);\nreturn msg;",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 360,
        "y": 780,
        "wires": [
            [
                "9ecd979073771698"
            ]
        ]
    },
    {
        "id": "89418712b3a4e644",
        "type": "inject",
        "z": "19ce8e091ec31145",
        "g": "02205f7eef6c2ea7",
        "name": "",
        "props": [
            {
                "p": "payload"
            },
            {
                "p": "topic",
                "vt": "str"
            }
        ],
        "repeat": "",
        "crontab": "",
        "once": false,
        "onceDelay": 0.1,
        "topic": "",
        "payload": "valve1",
        "payloadType": "str",
        "x": 130,
        "y": 780,
        "wires": [
            [
                "0596e3f2e8c9c4d6"
            ]
        ]
    },
    {
        "id": "9ecd979073771698",
        "type": "debug",
        "z": "19ce8e091ec31145",
        "g": "02205f7eef6c2ea7",
        "name": "debug 5",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "false",
        "statusVal": "",
        "statusType": "auto",
        "x": 600,
        "y": 780,
        "wires": []
    },
    {
        "id": "3435ab72215017d8",
        "type": "inject",
        "z": "19ce8e091ec31145",
        "g": "02205f7eef6c2ea7",
        "name": "",
        "props": [
            {
                "p": "payload"
            },
            {
                "p": "topic",
                "vt": "str"
            }
        ],
        "repeat": "",
        "crontab": "",
        "once": false,
        "onceDelay": 0.1,
        "topic": "",
        "payload": "valve1",
        "payloadType": "str",
        "x": 130,
        "y": 720,
        "wires": [
            [
                "020d332909f4e2ef"
            ]
        ]
    },
    {
        "id": "a7a1ab528ff10487",
        "type": "io7-hub",
        "name": "app",
        "host": "mqtt",
        "useTLS": false,
        "knownPort": true,
        "port": "1883",
        "tls": "",
        "clientid": ""
    },
    {
        "id": "d7383ea4332dbe4a",
        "type": "ui-group",
        "name": "Group 1",
        "page": "ea176c6d6123655d",
        "width": 4,
        "height": 1,
        "order": 1,
        "showTitle": true,
        "className": "",
        "visible": "true",
        "disabled": "false",
        "groupType": "default"
    },
    {
        "id": "ea176c6d6123655d",
        "type": "ui-page",
        "name": "Page 1",
        "ui": "1662b5c665ac1f70",
        "path": "/page1",
        "icon": "home",
        "layout": "grid",
        "theme": "0b60911df39b0f01",
        "breakpoints": [
            {
                "name": "Default",
                "px": "0",
                "cols": "3"
            },
            {
                "name": "Tablet",
                "px": "576",
                "cols": "6"
            },
            {
                "name": "Small Desktop",
                "px": "768",
                "cols": "9"
            },
            {
                "name": "Desktop",
                "px": "1024",
                "cols": "12"
            }
        ],
        "order": 1,
        "className": "",
        "visible": "true",
        "disabled": "false"
    },
    {
        "id": "1662b5c665ac1f70",
        "type": "ui-base",
        "name": "My Dashboard",
        "path": "/dashboard",
        "appIcon": "",
        "includeClientData": true,
        "acceptsClientConfig": [
            "ui-notification",
            "ui-control"
        ],
        "showPathInSidebar": false,
        "headerContent": "page",
        "navigationStyle": "default",
        "titleBarStyle": "default",
        "showReconnectNotification": true,
        "notificationDisplayTime": 1,
        "showDisconnectNotification": true,
        "allowInstall": true
    },
    {
        "id": "0b60911df39b0f01",
        "type": "ui-theme",
        "name": "Default Theme",
        "colors": {
            "surface": "#ffffff",
            "primary": "#0094CE",
            "bgPage": "#eeeeee",
            "groupBg": "#ffffff",
            "groupOutline": "#cccccc"
        },
        "sizes": {
            "density": "default",
            "pagePadding": "12px",
            "groupGap": "12px",
            "groupBorderRadius": "4px",
            "widgetGap": "12px"
        }
    },
    {
        "id": "ce4807d0d98f0912",
        "type": "global-config",
        "env": [],
        "modules": {
            "node-red-contrib-io7": "0.1.8",
            "@flowfuse/node-red-dashboard": "1.29.0"
        }
    }
]
