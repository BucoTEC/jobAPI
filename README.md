# jobAPI

This is a REST API build with Express.js and Mongo.db

It is used for job advertisement and it is configured to send and recive
      JSON data
    
    Models
    
    Job
      company: { type: String, required: [true, 'Please provide company name'],
      maxlength: 50, },
      position: { type: String, required: [true, 'Please provide position'],
      maxlength: 100, },
      status: { type: String, enum: ['interview', 'declined', 'pending'],
      default: 'pending', },
      createdBy: { type: mongoose.Types.ObjectId, ref: 'User', required: [true,
      'Please provide user'], },
      
    User
      name: { type: String, required: [true, "Please provide name"], maxlength:
      50, minlength: 3, },
      email: { type: String, required: [true, "Please provide email"], match: [
      /^(([^&lt;>()[\]\\.,;:\s@"]+(\.[^&gt;>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/,
      "Please provide a valid email", ], unique: true, },
      password: { type: String, required: [true, "Please provide password"],
      minlength: 6, },
      
    Routes

        POST /api/auth/register (takes req body with username, password and
        email)
        
        POST /api/auth/login (takes req body with email and password and sends
        back jwt token. The token is to be used as auth header with all other
        req)
        
        POST /api/jobs (takes req body with company and position and creates
        job)
        
        GET /api/jobs (get all jobs)
        
        GET /api/jobs/:id (findes one job based on req param)

        PATCH /api/jobs/:id (findes one job based on req param and updates with
        req body)
        
        DELETE /api/jobs/:id (findes one job based on req param and deletes it)
