---
layout: post
title: "如何获取用户的信息"
date: 2016-01-09 
description: "小程序的使用"
tag: 小程序

---
### 用户信息的获取

>* var appUserinfo;
>* var openid = '';
>* var sessionkey = '';
>* var encryptedData = '';
>* var iv = '';
>* App({
>* getUserInfo: function (callback) {
>* var retuser = {};
>* var that = this;
>*  wx.showLoading({ title: "加载中..." });
>*    wx.login({
>*      success: function (res) {
>*        var code = res.code;
>*        if (code) {
>*          wx.request({
>*            url: "https+aspx",// 通过获取code来换取session_key
>*            data: {
>*              code: code,
>*            },
>*            success: function (res) {//res返回值获得session_key&openid
>*              var retdata = res.data.data;
>*              openid = retdata.openid,
>*                sessionkey = retdata.session_key;

**设置用户信息**

>*              wx.getUserInfo(
>*                 success: function (res) {
>*                  encryptedData = res.encryptedData;
>*                   iv = res.iv;
>*                   appUserinfo = res.userInfo
>*                   wx.request({
>*                     url: "https+aspx",//通过session_key来换取公众号信息
>*                     data: {
>*                       openid:openid,
>*                       unionid:encryptedData,//解析unionid(md5加密&解密获得)
>*                       sessionkey:sessionkey,
>*                       iv:iv,
>*                       appid: 'wx758e9825590dc405'
>*                     },
>*                     dataType: "json",
>*                     success: function (ret) {
>*                       wx.hideLoading();
>*                       var retdata = ret.data;
>*                       for (var key in retdata) {
>*                         retuser[key] = retdata[key];
>*                       }
>*                       retuser.littleid = retuser.uid;//换取公众平台用户的id信息
>*                       retuser.openid=openid;
>*                       callback && callback(retuser);
>*                     }
>*                   });
>*                },
>*                 fail: function (res) {
>*                   var that = this
>* if(res){//res返回值来检查用户授权信息&重新授权
>*   wx.showModal({
>*     title: '警告',
>*     content: '若不授权微信登陆，您将无法使用商城部分功能,点击重新获取授权',
>*     success: function () { 
>*       wx.openSetting({
>*         success: function (res) {
>*         if (!res.authSetting["scope.userInfo"] || !res.authSetting["scope.userLocation"]) {
>*             wx.getUserInfo({})
>*           }
>*         }
>*       })
>*     }
>*   })
>* }
>*                 }
>*               })
>*            }
>*          });
>*        }
>*       }
>*     })
>* }
>* })
