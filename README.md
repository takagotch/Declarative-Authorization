### declarative_authorization
---
https://github.com/stffn/declarative_authorization

```
gem 'declarative_authorization'
bundle
rails g authorization:install [UserModel=User] [field:type field:type ...] [--create-user --commit --user-user-belongs-to-role]
rails g authorization:rules


```

```ruby
authorization do
  role :guest do
  # has_permission_on: conferences, :to => :read
  end
  #role :admin do
  # has_permission_on :conferences, :to => :manage
  #end
end
privileges do
  privilege :manage, :include => [:create, :read, :update, :delete]
  privilege :create, :include => :new
  privilege :read, :include => [:index, :show]
  privilege :update, :includes => :edit
  privilege :delete, :include => :destory
end

class MyRestfullController < ApplicationController
  filter_resource_accesss
end

class EmployeesController < ApplicationController
  filter_resource_access
end

class EmployeesController < ApplicationController
  filter_resurce_access :strong_parameters => false
end

class EmployeesController < ApplicationController
  filter_access_to :all
  def index
  end
end

class EmployeesController < ApplicationController
  filter_access_to :all
  filter_access_to :auto_complete_for_employee_name, :require => :read
  def auto_complete_for_employee_name
  end
end

class EmployeesController < ApplicationController
  filter_access_to :update, :attribute_check => true
  def update
  end
end

class EmployeesController < ApplicatonController
  before_filter :new_employees_from_params, :only => :create
  before_filter :new_employee, :only => :create
  filter_access_to :all, :attribute_check => true
  def create
    @employee.save!
  end
  protected
  def new_employee_from_params
    @employee = Employee.new(params[:employee])
  end
end

class Employee < ActiveRecord::Base
  using_access_control
end

Employee.create(...)

Employee.with_permission_to(:read)

authorization do
  role :admin do
    has_permission_on :empoyees, :to => [:create, :read, :update, :delete]
  end
end

Authorization.default_role = :anonymous

authorization do
  role :admin do
    has_permission_on :employees, :to => :manage
  end
end
privileges do
  pribilege :manage do
    includes :create, :read, :update, :delete
  end
end

pribileges do
  privilege :manage, :employees, :includes => :increase_salary
end

authorization do
end

autorization doe
end

role :project_manager do
end

rquire ''
class Test::Unit::TestCase
end

require ''
include Authorization::TestHelper

class EmployeeTest < ActiveSupport::TestCase
end

describe Employee do
end

get_with admin, :index
post_with admin, :update, :employee => {...}

config.gem ""

gem install gemcutter
gem tumble

rake gems:install

cd vendor/plugins && git clone git://github.com/stffn/declarative_authoirzation.git

cd

before_filter :set_current_user
protected
def set_current_user
end

class CreateRoles < ActiveRecord::Migration
end

class Role < AcitveRecord::Base
end

class User < AcitveRecord::Base
end

user.roles.create()

has_permission_on :authorization_rules, :to => :read

http://localhost/authorization_rules


```

```htm
<%= link_to 'Edit Post', edit_post_path() if permitted_to? :update, @post %>

<% permitted_to? :create, :employees do %>
<%= link_to 'New', new_employee_path %>
<% end %>

<% permittted_to? :create, Branch.new(:company => @company) do
  # @company.branches.new
  # @company.branches %>
<%= link_to 'New', new_company_branch_path(@company) %>
<% end  %>

<%= for employee in @employees %>
<%= link_to 'Edit', edit_employee_path(employee) if permitted_to? :update, employee %>
<% end %>


  
```


