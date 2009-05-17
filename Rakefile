desc "Get info for featured projects"
task :featured do
  require 'restclient'
  require 'octopi'

  projects = RestClient.get("http://gist.github.com/39099.txt").split("\n").map { |p| p.split("/") }

  File.open("_includes/featured.html", "w") do |f|
    projects.reverse[0..15].each do |project|
      p project
      repo = Octopi::User.find(project.first).repository(project.last)
      f.write <<EOF
<div class='repo'>
  <h3><a href='#{repo.url}'>#{repo.name}</a></h3>
  <span class='desc'>#{repo.description}</span>
</div>
EOF
    end
  end
end
