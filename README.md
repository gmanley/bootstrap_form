bootstrap_form
==============

bootstrap_form is a rails form builder that makes it super easy to create beautiful-looking forms using Twitter Bootstrap 2.0


Requirements
------------

* Ruby 1.9+
* Rails 3.1+
* Twitter Bootstrap 2.0+


Installation
------------

Add the gem to your Gemfile

    gem 'bootstrap_form'

Install the gem

    bundle

Add bootstrap_form to your application.css file

    /*
     *= require bootstrap_form
    */
    
This brings in a couple of minor css classes that help format helper and
error messages.

Usage
-----

    <%= bootstrap_form_for(@user) do |f| %>
      ...
    <% end %>

This plugin provides the following form helpers:

* text_field
* password_field
* text_area
* file_field
* number_field
* email_field
* telephone_field (phone_field)
* url_field
* select
* collection_select
* date_select
* time_select
* datetime_select
* check_box

These form helpers accept the same options as the Rails form
helpers with the addition of two options `label` and `help`. Here's an
example form that also uses the `actions` helper for the submit button:

    <%= bootstrap_form_for(@user) do |f| %>
      <%= f.alert_message "Please fix the errors below." %>

      <%= f.text_field :email, autofocus: :true %>
      <%= f.password_field :password, help: 'Must be at least 6 characters long' %>
      <%= f.password_field :password_confirmation, label: 'Confirm Password' %>
      <%= f.check_box :terms, label: 'I agree to the Terms of Service' %>

      <%= f.actions do %>
        <%= f.primary 'Sign Up', disable_with: 'Saving...' %>
      <% end %>
    <% end %>

![Example Form](https://github.com/potenza/bootstrap_form/raw/master/examples/example_form.png)


Options
-------

To use a horizontal-style form with labels to the left of the inputs,
add the `.form-horizontal` class:

    <%= bootstrap_form_for(@user, html: { class: 'form-horizontal' }) do |f| %>

To place helper text underneath the fields, pass the option `help:
:block`:

    <%= bootstrap_form_for(@user, help: block) do |f| %>

Here's an example of a horizontal-style form with block helpers:

![Example Form](https://github.com/potenza/bootstrap_form/raw/master/examples/example_horizontal_block_form.png)


Custom Controls
---------------

If you have a custom form control or content that you want to wrap 
in Bootstrap-style form markup, you can do the following:
  
    <%= f.control_group "Custom Field" do %>
      <span>My Custom Field</span>
    <% end %>

which will output the following:

    <div class="control-group">
      <label class="control-label">Custom Field</label>
      <div class="controls">
        <span>My Custom Field</span>
      </div>
    </div>

You can also specify the label's for attribute like this:

    <%= f.control_group "Custom Field", for: 'custom-control' do %>
      <span>My Custom Field</span>
    <% end %>
  

Validation Errors
-----------------

When a validation error is triggered, the field will be outlined and the
error will be displayed next to the field. Rails normally wraps fields
in a div (field_with_errors), but this behavior is suppressed when `bootstrap_form_for` is called.

![Example form with errors](https://github.com/potenza/bootstrap_form/raw/master/examples/example_form_error.png)


Credits
-------

Inspired by Ryan Bates' [Form Builder
Railscast](http://railscasts.com/episodes/311-form-builders)

bootstrap_form is Copyright (c) 2012 Stephen Potenza and is distributed under the MIT license.
