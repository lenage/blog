---
layout: post
title: Rails helper and helper_method in Controller
category: tech
---
## helper_method
defined in `rails/actionpack/lib/abstract_controller/helpers.rb`
Declare a controller method as a helper. For example, the following

{% highlight ruby %}
    class ApplicationController < ActionController::Base
      helper_method :current_user, :logged_in?

      def current_user
        @current_user ||= User.find_by_id(session[:user])
      end

      def logged_in?
        current_user != nil
      end
    end
{% endhighlight %}

then in view

    <% if logged_in? -%>Welcome, <%= current_user.name %><% end -%>

## helper
The `helper` class method can take a series of helper module names, a block, or both.

###Parameters
* **\*args** - Module, Symbol, String, :all
* **block** - A block defining helper methods
