require "dotenv"
require "mediumite"
require "pathname"
require "stringex"

Dotenv.load

desc "Begin a new post in ./posts folder with markdown extension"
task :new do
  puts "Enter a title for your post: "
  title = STDIN.gets.chomp

  filename = "posts/#{Time.now.strftime('%Y-%m-%d')}-#{title.to_url}.md"
  abort("Oops file #{filename} already exists!") if File.exists?(filename)

  puts "Creating new post: #{filename}"
  open(filename, "w") do |post|
    post.puts "# #{title}"
  end

  system("#{ENV['EDITOR']} #{filename}") if ENV["EDITOR"]
end

desc "Create a post as a draft"
task :upload do
  MAX_DISPLAY_POST_COUNT = 5

  pathnames = Dir.glob("./posts/*").sort_by(&File.method(:ctime)).reverse.map { |filename| Pathname.new(filename) }.take(MAX_DISPLAY_POST_COUNT)
  if pathnames.empty?
    puts "We don't have any posts yet"
    next
  end

  index = 0
  loop do
    pathnames.each.with_index(1) { |file, index|
      puts "#{index}: #{file.basename}"
    }
    print "Which post do you want to upload? (index): "
    index = STDIN.gets.chomp.to_i
    break if (1..[pathnames.size, MAX_DISPLAY_POST_COUNT].min).include?(index)
    print "#{index} is not valid.\n\n"
  end

  open(pathnames[index - 1]) do |file|
    client = Mediumite::Client.new(token: ENV["MEDIUM_ACCESS_TOKEN"])
    post = Mediumite::Post.new(title: "", body: file.read)
    response = client.create_post(post)
    puts "#{response.title} was created: #{response.url}"
    sh "open #{response.url}"
  end
end
