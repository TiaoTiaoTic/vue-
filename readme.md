#用和风天气api制作的vue3天气小组件
##简介
展示当地天气和一些额外和天气有关的信息。
##使用方法
1.把组件复制，用到你的项目中；
2.注意组件的data中的hefengWeatherKey需要自己去和风天气官网去申请一下。和风天气官网：https://dev.qweather.com/；
3.跨域问题需要解决。开发过程中是用webpack设置中的proxy解决的，也就是用devserver，这里把我的配置贴出来：
  devServer:{
    open:true,
    proxy:{
      '/api':{
        target:'https://devapi.qweather.com',
        ws:false,
        changeOrigin: true,
        secure: true,
        pathRewrite: {
            '^/api': '',
        },
      },
      '/geoapi':{
        target:'https://geoapi.qweather.com',
        ws:false,
        changeOrigin:true,
        pathRewrite:{
          '^/geoapi':'',
        }
      },
      '/getCityName':{
        target:'http://pv.sohu.com/cityjson?ie=utf-8',
        ws:false,
        changeOrigin:true,
        pathRewrite:{
          '^/getCityName':'',
        }
      }
    }
  }