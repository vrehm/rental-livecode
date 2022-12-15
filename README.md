



https://kitt.lewagon.com/knowledge/tutorials/rails_api
https://dev.to/nemwelboniface/api-with-rails-7-ngh

`rails new rental-api --api --database=postgresql --skip-test`
`cd rental-api`
`code .`
`rails db:create`
`rails g model Listing num_rooms:integer #:default(1), #:null:false`

`rails g model Booking listing:references start_date:date end_date:date #:null:false x 2`
`add_index :bookings, [:listing_id, :start_date, :end_date], unique: true`

`rails g model Reservation listing:references start_date:date end_date:date #:null:false x 2`
`add_index :reservations, [:listing_id, :start_date, :end_date], unique: true`

`rails g model Mission listing:references date:date mission_type:integer price:integer #:null:false x 3, default 0`
`add_index :missions, [:listing_id, :date, :mission_type], unique: true`

add listing associations has_many :bookings, has_many :reservations, has_many :missions
  and dependent: :destroy

`rails db:migrate`
update 'db/seeds.rb'

validations des models
callback des models

routing api avec namespace
controller api listings
controller api missions