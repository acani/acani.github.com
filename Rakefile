# usage rake post[my-new-post] or rake post['my new post'] or rake post (defaults to "new-post")
desc "Begin a new post in _posts dir"
task :post, :title do |t, args|
  args.with_defaults(:title => 'new-post')
  slug = args.title.strip.downcase.#gsub(/(&|&amp;)/, ' and ').
         gsub(/[\s\.\/\\]/, '-').gsub(/[^\w-]/, '').gsub(/[-_]{2,}/, '-').
         gsub(/^[-_]/, '').gsub(/[-_]$/, '')
  file = "_posts/#{Time.now.strftime('%Y-%m-%d')}-#{slug}.md"
  open(file, 'w') do |post|
    post.puts "---"
    post.puts "layout: post"
    post.puts "title: \"#{args.title}\""
    post.puts "---"
  end
  system("e #{file}")
end
