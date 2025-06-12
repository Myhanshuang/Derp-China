# 几个坑点

1、选择 snap Certbot，不会出一堆问题

2、tailscale那部分添加如下：

```
"derpMap": {
		// OmitDefaultRegions 设为 false, 意味着在用你的DERP的同时,
		// 也保留官方的DERP作为备用, 这样更稳定。
		"OmitDefaultRegions": false,

		"Regions": {
			// 这是一个自定义的区域ID, 必须大于900。901是个不错的选择。
			"901": {
				"RegionID":   901,
				"RegionCode": "myderp",
				"RegionName": "My DERP Server", // 可以改成任何你喜欢的名字
				"Nodes": [
					{
						"Name":     "1", // 节点名字, 保持为 "1" 即可
						"RegionID": 901,
						// 关键修改: 改为您的域名
						"DERPPort": 442,
						"HostName": "derp.acacia.website",
					},
				],
			},
		},
	}
```

3、记得90天key到期
