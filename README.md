# MongoBlogger

const getUUID = () => {
    const max = 40
    const min = 0
    const randIndex = Math.floor(Math.random() * (max - min + 1) + min)
    const uuidList = [
        "239fc1f4-9a65-4774-afe1-c4f7626a5ad1",
        "ee8ae23c-2e26-4b0b-b294-c3d0ca4850ef",
        "fb1b7a41-ca45-47b5-84f7-64f27b38249b",
        "a4edc658-3525-4205-9f17-c37d9c897676",
        "043328c9-1e49-42c1-ac88-8177eb548b81",
        "9d585fa2-4d75-43af-857c-a3111c3ad732",
        "c2d455d4-a0ff-4a07-8e04-098371240003",
        "81636fb8-c3b3-46b0-952f-8f5c3cf9a87d",
        "25f41810-131b-40af-b163-738ea01781d4",
        "15e478a8-b4dc-4433-a681-80d2c66f28e2",
        "9dde5a1d-1792-43f7-b2a0-1afad837c77f",
        "8b6fa098-d1cb-47ee-9d60-4dbc6b79a1c5",
        "35a04237-507c-45f5-b770-3ce2c2fd088b",
        "b759942f-2fcb-467e-8f25-3873d357171e",
        "abcced87-72e1-46dd-b026-0b2b1e3c52bc",
        "a1b3fb6e-ba2f-4614-8b4a-e7c482398982",
        "09e854b1-9b78-4e01-97f7-e54cb511605a",
        "92744be8-81db-4598-8693-1b2d756189a8",
        "23d3563e-a211-4759-a77e-6de55d1e03ac",
        "f95b8b6e-4552-4fca-a6c5-1b2588468b6e",
        "e8d3df08-d1ca-41b0-a008-47754639ac98",
        "53985bf3-1eec-448b-ad63-72e89baa1ea0",
        "ebec6418-9540-437a-bbd0-bb552dfe2d63",
        "4cc02e40-895a-442a-a58d-7956c12f535d",
        "61e9e0da-2bf6-4b3b-adb2-b03326d1d7a9",
        "eb4ce320-bc4f-4446-97e6-d42b6ace857f",
        "f63daa0b-eb0b-47ff-91cb-cead351d87f5",
        "8d850030-d5d0-47c6-8ed5-a5265c166cb4",
        "68a8922a-3a69-49b5-bb2c-5cca7ecc9b8e",
        "81dac8b1-06c7-40f9-94c7-ceeefa3a3475",
        "afd45ade-0a6f-4a95-bdb2-5d720d1cdd25",
        "5bb8d076-fa3e-4802-bbf2-f4671156a2ad",
        "ad9ead68-c96d-4f7f-b246-6eb07b203743",
        "07c59493-0a54-4477-8ae6-e23b01c4cb48",
        "7841e93c-0bdc-4b6b-a5c4-512e280e5aa8",
        "4387f4d8-aeac-4559-9f1b-3c5d537c955c",
        "e365f13c-4c1d-4ee1-8a66-3dbbbab71f0d",
        "08dd1f20-7d31-4120-89ed-343d4006a7cb",
        "98a06f8f-50c9-4832-9d2d-daa45543db00",
        "7c5d70bb-2a00-4009-9bb8-1bb163fb501f",
    ]
    return uuidList[randIndex]
}

/*
********************************************* NUMBER ONE ********************************************************
*/

// const getPosts = (searchObject, sortObject, limit, skip) => {
//     const posts = db.BlogsDB.find(searchObject).toArray()
//     return posts
// }

// const searchObject = {}
// const sortObject = {}
// const limit = 10
// const skip = 0
// searchObject.createdAt = {$gt: new Date("2022/05/01")}

// // Uncomment the following line when you're ready to run getPosts
// const posts = getPosts(searchObject, sortObject, limit, skip)
// console.log(posts)

/* 
Requirements:
    COMPLETED - Update searchObject so that the query in getPosts searches for all posts with a createdAt date greater than May 1, 2022
Stretch goals: 
    - Update the code in getPosts to chain the .sort() method with the sortObject passed as an argument onto .find() so that the 
        function sorts the results. I.E. if sortObject = {lastModified: -1} then the result from getPosts should be sorted by 
        lastModified in descending order.
    - Update the code in getPosts to chain .limit() and .skip() on the results so that the search result will only return the 
        inputted limit number of posts and skip the inputted skip number of posts.
    - Update the code in getPosts so that if any of the arguments sortObject, limit and skip are undefined, the function will 
        still execute with the other arguments that are defined.
*/


/*
********************************************* NUMBER TWO ********************************************************
*/

const createPost = (newPost) => {
    const id = getUUID()
    const postData = {
        createdAt: new Date(),
        title: newPost.title,
        text: newPost.text,
        author: newPost.author,
        categories: newPost.categories,
        lastModified: new Date(),
        id: getUUID()
       
    }
    db.BlogsDB.insertOne(postData)
}

const newPost = {
    title: "The Dark Knight Movie Review",
    text: "This movie was amazing because I am Batman.",
    author: "Bruce Wayne",
    categories: ["superhero", "action", "thriller"]
}

// Uncomment the following line when you're ready to run createPosts
// createPost(newPost)

/*
Requirements:
  COMPLETED - Add code in createPost so that a new blog post will be created when createPost is called.
    Note: id, createdAt and lastModified will have to be generated. The id field can be generated with the provided getUUID() 
        function which will return a random UUID.
Stretch Goal: 
    - Add validation in createPost so that if postData does not have the required fields of title, text, author, and categories, 
        it throws an error
*/

/*
********************************************* NUMBER THREE ********************************************************
*/

const updatePost = (id, newPostData) => {
    console.log(id)
    console.log(postId)
    db.BlogsDB.updateOne({
        id: postId
    }, {
        $set: { title: newPostData.title,
            text: newPostData.text,
            author: newPostData.author,
            categories: newPostData.categories,
            lastModified: new Date()}
    }) // Update this line with your code
}

const updatedPost = {
    title: "The Dark Knight Movie Review",
    text: "This movie was amazing because I am Batman, and totally not Bruce Wayne. I don't even know who that is.",
    author: "Batman",
    categories: ["superhero", "action", "thriller"]
}
const postId = "08dd1f20-7d31-4120-89ed-343d4006a7cb" // This variable should be the uuid of the blog post you created before using createPost

// Uncomment the following line when you're ready to run updatePost
// updatePost(postId, updatedPost)

/*
Requirements:
    - Add code in updatePost so that Mongo will find the post created before using createPost and update it to the new data 
        in updatedPost. 
    Note: You will need to change the postId variable to be the UUID given to the blog post you created before using createPost(). 
        This value can be hardcoded in the postId variable, E.G. const postId = "fb1b7a41-ca45-47b5-84f7-64f27b38249b".
Stretch Goal:
    - Use getPosts() to find the blog post you created before and get the UUID from the id field in that blog post 
        programmatically without needing to hardcode the postId variable. 
*/


/*
********************************************* NUMBER FOUR ********************************************************
*/


const deletePost = (id) => {
   db.BlogsDB.deleteOne({
       id: postId
   })
}

const postIdToDelete = "08dd1f20-7d31-4120-89ed-343d4006a7cb"

// Uncomment the following line when you're ready to run deletePost
deletePost(postIdToDelete)

/*
Requirements:
    - Add code in deletePost so that it will find a post by the given id and delete it.
Stretch Goal:
    - Write a new function deletePosts that takes an array of ids as an argument and deletes all of the posts with those ids.
*/