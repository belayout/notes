##notes
#学习《第一行代码》的一些零碎笔记
  
  今天在学习第一行代码时用到了Notification.setLatestEventInfo()，然后就报错了，看了看报错原因再加上查询后得知：setLatestEventInfo该方法已被deprecate，不建议使用了。
  看完了网上那么多解释后总结一下：(参考资料：http://blog.csdn.net/ankechen/article/details/8637365)
  
  >1.低于API Level 11版本，也就是Android 2.3.3以下的系统中，setLatestEventInfo()函数是唯一的实现方法。
    
  >2.高于API Level 11，低于API Level 16 (Android 4.1.2)版本的系统中，可使用Notification.Builder来构造函数。但要使用getNotification()来使notification实现。此时，前面版本在notification中设置的Flags，icon等属性都已经无效，要在builder里面设置。
  <pre><code>Notification.Builder builder = new Notification.Builder(context)  
            .setAutoCancel(true)  
            .setContentTitle("title")  
            .setContentText("describe")  
            .setContentIntent(pendingIntent)  
            .setSmallIcon(R.drawable.ic_launcher)  
            .setWhen(System.currentTimeMillis())  
            .setOngoing(true);  
            notification=builder.getNotification();  </code></pre>
  >3.高于API Level 16的版本，就可以用Builder和build()函数来配套的方便使用notification了。 
  <pre><code>Notification notification = new Notification.Builder(context)    
         .setAutoCancel(true)    
         .setContentTitle("title")    
         .setContentText("describe")    
         .setContentIntent(pendingIntent)    
         .setSmallIcon(R.drawable.ic_launcher)    
         .setWhen(System.currentTimeMillis())    
         .build();   </code></pre>
  
  还有关于Notification的其他属性，我觉得这篇写的真好：http://blog.csdn.net/vipzjyno1/article/details/25248021，mark一下。
