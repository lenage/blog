---
layout: post
title: Rails helper and helper_method in Controller
category: tech
---
## helper_method
defined in `rails/actionpack/lib/abstract_controller/helpers.rb`
Declare a controller method as a helper. For example, the following

    class ApplicationController < ActionController::Base
      helper_method :current_user, :logged_in?

      def current_user
        @current_user ||= User.find_by_id(session[:user])
      end

      def logged_in?
        current_user != nil
      end
    end

then in view

    <% if logged_in? -%>Welcome, <%= current_user.name %><% end -%>


## helper
The +helper+ class method can take a series of helper module names, a block, or both.

###Parameters
* <tt>*args</tt> - Module, Symbol, String, :all
* <tt>block</tt> - A block defining helper methods
