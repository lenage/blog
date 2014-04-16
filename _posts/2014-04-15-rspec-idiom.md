---
layout: post
title: Rspec小记
category: blog,tech
tags: rails, Rspec
published: false
---

### let
`let(:name) { expression }`简单的定义全局变量, 该定义的block是lazy的，
也就是说只在有显式调用name的时候才执行expression, 如果想让block立即执行，
要用`let!(:name) { expression }`

~~~ ruby
describe BlogPost do
  before do
    @blog_post = BlogPost.new :title => 'Hello'
  end
  it "dose something" do
    @blog_post.should ...
  end

  it "dose something else" do
    @blog_post.should ...
  end
end
~~~

换成let

~~~ ruby
describe BlogPost do
  let(:blog_post) {  BlogPost.new :title => 'Hello' }

  it "dose something" do
    blog_post.should ...
  end

  it "dose something else" do
    blog_post.should ...
  end
end
~~~

### specify
`it`的alias,为了更好的语义化，如：

~~~ ruby
describe BlogPost do
  before { @blog_post = BlogPost.new :title => "foo"}

  it "should not be publsihed" do
    @blog_post.should_not be_published
  end
end
~~~

可以写成:

~~~ ruby
describe BlogPost do
  let(:blog_post) { BlogPost.new :title => "foo" }
  specify { blog_post.should_not be_published }
end
~~~

### expect
expect用在需要改变某个值或者抛出异常的时候

~~~ ruby
expect {
  BlogPost.create :title => "Hello"
}.to change { BlogPost.count }.by(1)

describe "#publish!" do
  let(:blog_post) { BlogPost.create :title => "Hello" }

  it "update published_on date" do
    expect {
      blog_post.publish!
    }.to change { blog_post.published_on }.from(nil).to(Date.today)
  end
end
~~~
