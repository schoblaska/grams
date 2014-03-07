require "./bootstrap"

task :console do
  binding.pry
end

task :create_subscription do
  lat = ENV["LAT"] || raise("You must supply a LAT")
  lng = ENV["LNG"] || raise("You must supply a LNG")
  radius = ENV["RADIUS"] || raise("You must supply a RADIUS")

  `curl -F 'client_id=#{Grams::Settings[:instagram_client_id]}' \
     -F 'client_secret=#{Grams::Settings[:instagram_client_secret]}' \
     -F 'object=geography' \
     -F 'aspect=media' \
     -F 'verify_token=#{Grams::Settings[:instagram_client_secret]}' \
     -F 'lat=#{lat}' \
     -F 'lng=#{lng}' \
     -F 'radius=#{radius}' \
     -F 'callback_url=#{URI.join(Grams::Settings[:public_url], "/realtime")}' \
     https://api.instagram.com/v1/subscriptions/`
end

task :remove_subscriptions do
  `curl -X DELETE 'https://api.instagram.com/v1/subscriptions?client_secret=#{Grams::Settings[:instagram_client_secret]}&object=all&client_id=#{Grams::Settings[:instagram_client_id]}'`
end