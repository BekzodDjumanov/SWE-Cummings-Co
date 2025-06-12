# SWE-Cummings-Co
Repo for SWE Internship
    ```pub fn get_rand_ipv6(subnet: &str) -> IpAddr {
    let (ipv6, prefix_len) = match subnet.parse::<Ipv6Cidr>() {
        Ok(cidr) => {
            let ipv6 = cidr.first_address();
            let length = cidr.networklength();
            (ipv6, length)
        }
        Err() => {
            panic!("invalid IPv6 subnet");
        }
    };```

    let ipv6_u128: u128 = u128::from(ipv6);
    let rand: u128 = random();

    let net_part = (ipv6_u128 >> (128 - prefix_len)) << (128 - prefix_len);
    let host_part = (rand << prefix_len) >> prefix_len;
    let result = net_part | host_part;

    IpAddr::V6(Ipv6Addr::from(result))
}

```pub fn create_client(subnet: &str, user_agent: &str) -> Client {```
    ```let ip = get_rand_ipv6(subnet);```

    Client::builder()
        .redirect(redirect::Policy::none())
        .danger_accept_invalid_certs(true)
        .user_agent(user_agent)
        .local_address(Some(ip))
        .build().unwrap()
}

Routing IPv6 through NI and using requests for selecting a randomized IP Address.```

BruteForce Method
