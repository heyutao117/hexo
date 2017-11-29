---
layout: layout
title: socket传值含义
date: 2017-11-24 16:29:17
tags:
---

<h1>socket常见几种消息</h1>
<h3>1.isPersonOnline</h3>
<p>isPersonOnline判断上次应用关闭时属于接单或者未打开接单的状态
<pre>{"isPersonOnline":false,"code":200,"lastSyncDt":"2017-11-21 14:11:28","action":"CHECK_STATE","requests":[]}</pre>
<pre>{"isPersonOnline":true,"code":200,"lastSyncDt":"2017-11-21 14:26:10","action":"CHECK_STATE","requests":[]}</pre>
</p>

<h3>2.RECEIVE_REQUEST</h3>
<p>action:RECEIVE_REQUEST 点击接单按钮后将这个状态传给后台
<pre>{"action":"RECEIVE_REQUEST","imei":"B1F39FDE-B548-4958-8D87-6952C80C10AC","point":{"radius":"65.000000","speed":"0","appVersion":"1.2.0","longituide":114.06235890742887,"power":"100","latituide":22.539048611573666,"recordTime":"2017-11-23 14:30:19","direction":"0","seq":"1511418619"},"phoneOs":"11.000000","phoneType":"iPhone 6","token":"fbdc434f-258a-443b-a82e-58e69edfa604%2386","requestId":"23430","networkType":"wifi"}</pre></p>
<h3>3.CANCELED</h3>
<p>cammad 取消<pre>{"personId":1524,"requestId":23420,"cancelReason":"客户自行取消：","command":"CANCELED","reqType":"VI"}</pre></p>
<h3>4.DISPATCH_ACK</h3>
<p>DISPATCH_ACK：APP收到接单信息
<pre>{"point":{"radius":"65.000000","speed":"0","appVersion":"1.2.0","longituide":114.06236042526861,"power":"100","latituide":22.539046782834429,"recordTime":"2017-11-23 16:58:03","direction":"0","seq":"1511427483"},"requestId":23534,"actionTime":"2017-11-23 17:12:59","token":"fbdc434f-258a-443b-a82e-58e69edfa604%2386","action":"DISPATCH_ACK"}</pre></p>
<h3>5.IGNORE_REQUEST</h3>
<p>IGNORE_REQUEST派单平台取消订单<pre>{"point":{"radius":"65.000000","speed":"0","appVersion":"1.2.0","longituide":114.06236042526861,"power":"100","latituide":22.539046782834429,"recordTime":"2017-11-23 16:58:03","direction":"0","seq":"1511427483"},"requestId":23534,"token":"fbdc434f-258a-443b-a82e-58e69edfa604%2386","action":"IGNORE_REQUEST"}</pre></p>


