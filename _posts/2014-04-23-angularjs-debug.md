---
layout: post
title: Angularjs debug
category: tech
---
在Angular js的scope中用watch查看输出和变化:

~~~javascript
  $scope.cart = 1;
  $scope.$watch('cart', function() {
    console.log('=========='+ (new Date) + '======');
    console.log($scope.cart);
  });
~~~
