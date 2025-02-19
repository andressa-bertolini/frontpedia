```
const filteredUsers = usersList.filter((user) =>
    user.includes(text),
);
```

Example:
```
const Home = () => {
    const [posts, setPosts] = useState([
        { title: "Post 1", body: "Lorem Ipsum...", author: "Tom", id: 1 },
        { title: "Post 2", body: "Lorem Ipsum...", author: "Andrew", id: 2 },
        { title: "Post 3", body: "Lorem Ipsum...", author: "Tobey", id: 3 }
    ]);

    // Filtra os posts do autor Tom
    const filteredPosts = posts.filter((post) => post.author === "Tom");

    return (
        <div className="home">
            {filteredPosts.map((post) => (
                <Post key={post.id} post={post} />
            ))}
        </div>
    );
};
```