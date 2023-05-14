# User_Mock_Data
This is a mock user data that can be used in projects which benefit from MongoDB.

In this schema, each user has a name consisting of a first name and a last name, an avatar URL, a birthday, a username, an email address, and a password. The user's profile includes a bio, follow information, page type, and post information. The follow information includes a list of user IDs for friend requests, followed users, followers, and blocked users. The page type can be either "public" or "private," and the post information is a list of post IDs.

------------------------------------------------------------------
```
{
    name: {
        firstName: String,
        lastName: String
    },
    avatar_url: String,
    birthday: Date,
    username: String,
    email: String,
    password: String,
    profile: {
        bio: String,
        followInfo: {
            requests: [{ type: mongoose.Schema.Types.ObjectId, ref: 'User' }],
            following: [{ type: mongoose.Schema.Types.ObjectId, ref: 'User' }],
            followers: [{ type: mongoose.Schema.Types.ObjectId, ref: 'User' }],
            blockList: [{ type: mongoose.Schema.Types.ObjectId, ref: 'User' }]
        },
        pageType: { type: String, enum: ['public', 'private'] },
        postsInfo: [{ type: mongoose.Schema.Types.ObjectId, ref: 'Post' }]
    },
    timestamp: { type: Date, default: Date.now }
}
```
