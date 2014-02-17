require 'rake'
require 'my_docker_rake/tasks'
include MyDockerRake::Utilities


MyDockerRake::Tasks.new do |c|
  c.containers = [{
    image: 'hyone/ubuntu',
    name: 'hyone.ubuntu'
  }]

  c.after_build = <<-EOC
    docker tag hyone/ubuntu:12.04 hyone/ubuntu
  EOC
end
